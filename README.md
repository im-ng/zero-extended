# Zero Soaking

A walkthrough of how we soak the [zero](https://gitea.pi/ng/zero.git) framework, from a single commit to a report anyone can open.

## Why we soak

Most tests run for milliseconds. A request comes in, we check the answer, and we move on. That misses the bugs that only appear after an hour: a slow memory leak, a backend that never recovers after a network blip, an allocator that forgets to free.

Soak testing runs the framework's own examples under real load for minutes to hours. We watch three things:

- Does memory **plateau** or keep **climbing**?
- Does the server **survive** a backend going dark?
- Does the **debug allocator** catch a leak?

For a web framework this matters because the examples are the contract. If `zero-basic` leaks under load, every app built on it leaks too. A soak is how we find that before a user does.

## The path from commit to report

Here is the real flow. You write code, and a chain of mirrors and triggers turns it into a published report.

![zero_soaking CI/CD flow](./resources/pele.svg)

### Step by step

1. **You commit to GitHub.** This is the only step you do by hand.
2. **GitHub mirrors to local Gitea.** Our mirror pushes the commit to `gitea.pi/ng/zero-soak`, the Gitea instance that Drone watches.
3. **Gitea triggers Drone.** A webhook fires on the push. Drone picks one of two pipelines:
   - `gate` runs on every push and PR — fast, covers every example for a short window.
   - `soak` runs on a nightly cron — picks one example and runs it for hours.
4. **Drone runs the soak.** The pipeline clones the zero framework at run time, runs unit validation, then `soak_all.sh` drives each example through three phases: a release build under load (watching RSS), a chaos phase that blackholes a backend and checks recovery, and a debug build that fails on any leak. The README covers these phases in depth.
5. **report.py trims the logs.** The raw server log is huge — hundreds of megabytes of repeated request lines. `trim_log` (`soak/report.py`) keeps the first and last 50 lines and drops the middle, so the published report stays small and portable. The full local log is left untouched for deep debugging.
6. **The publish step exports the report.** It pushes `soak/report/` to GitHub Pages on `im-ng/zero-extended` (the `reports` branch). Your report is now on the web.

## What you get

You open the dashboard. A banner tells you overall pass or fail. Each example has a row: status, backends, chaos result, RSS growth, and links to the trimmed logs. Expand a row to see every check, pass or fail.

- If RSS climbed past the threshold, the row shows a **leak signal** with the exact growth in KiB.
- If the debug allocator found a leak, the build failed and the log shows where.
- If a backend dropped and the server recovered, the chaos check is green.

The same data ships as `report.md`, handy for pasting into a PR comment.

## Lengthy Conversation

Soak testing is just a long, honest conversation with the framework. The flow above is what keeps that conversation automatic.
