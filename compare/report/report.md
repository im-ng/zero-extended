# zero head-to-head scorecard

> Gate smoke · generated 2026-11-25 04:14 UTC · positioning, not ranking. Every axis names its own winner; losses stay visible.

## Executive summary

| Framework | Axes won |
|---|---:|
| zero | 8 of 10 |
| gofr | 1 of 10 |
| fastapi | 0 of 10 |
| axum | 1 of 10 |

zero leads read-heavy throughput with **8,081 req/s** (6.2× GoFr). Remaining losses are listed in [Where we are behind](#where-we-are-behind-and-what-to-fix).


## Honest scorecard (median of runs; raw JSON retained)

| Metric | zero | gofr | fastapi | axum | Best |
|---|---:|---:|---:|---:|---|
| p50 [read-heavy] | 3.17 | 19.59 | 526.99 | 50.14 | zero |
| p95 [read-heavy] | 12.62 | 80.86 | 908.00 | 70.97 | zero |
| p99 [read-heavy] | 22.02 | 126.56 | 950.96 | 78.63 | zero |
| rps [read-heavy] | 8081.00 | 1313.25 | 71.90 | 739.36 | zero |
| errors [read-heavy] | 0.00 | 0.00 | 0.00 | 0.00 | zero |
| p50 [balanced] | 6.92 | 20.87 | 46.53 | 63.95 | zero |
| p95 [balanced] | 128.08 | 91.27 | 1835.99 | 107.79 | gofr |
| p99 [balanced] | 495.76 | 141.70 | 1929.05 | 132.08 | axum |
| rps [balanced] | 1218.07 | 1213.32 | 78.91 | 547.07 | zero |
| errors [balanced] | 0.00 | 0.00 | 0.00 | 0.00 | zero |

Latency in ms, throughput in req/s, errors as a rate. Percentiles use the steady stage only (warmup/spike excluded; the window is derived from each run's own timestamps, so the 10 s smoke gate and 60 s bench are both correct).


> Gate-smoke runs (`round=smoke`) are included for visibility. They are threshold checks with a 10 s steady stage, **not** publishable bench numbers.

## Footprint & breadth tax

| Framework | Idle MiB | Peak MiB | Cold start s | Binary MiB | Deps | Config lines | App LOC |
|---|---:|---:|---:|---:|---:|---:|---:|
| zero | 44.22 | 63.64 | 0.00 | 32.67 | 1 | 22 | 236 |
| gofr | 33.00 | 53.56 | 0.00 | 55.86 | 101 | 14 | 161 |
| fastapi | 36.60 | 64.81 | 1.00 | — | 2 | 20 | 87 |
| axum | 5.22 | 17.16 | 1.00 | 3.30 | 14 | 5 | 151 |

## Run configuration

The only intentional difference is how each stack waits for a free SQLite connection. Everything else is held constant.

| | zero | gofr | fastapi | axum |
|---|---|---|---|---|
| Connections | 4 (`SQLITE_POOL_SIZE`) | 1 (`DB_MAX_OPEN_CONNECTION`) | 1 per request | 1 (`max_connections`) |
| If all busy | waits | queues | opens a new one | queues |

Held constant: WAL journal, `NORMAL` sync, 5 s busy timeout, 1 process (1 uvicorn worker).

- **zero build:** ReleaseFast (see `results/zero/zero.version.json`)
- **Logging:** quiet — zero logs nothing, gofr fatal, fastapi critical, axum off (`COMPARE_QUIET_LOGS=1`; flip to `0` to change)
- **Timeouts:** health gate 120 s; k6 10 s warmup + 10 s steady + 10 s spike; pass = under 1% failed requests and p95 under 2 s

> Check the **errors** row before believing a latency or RPS win. A pool that fails instead of waiting makes the survivors look fast.


## Design internals (framework-level evidence)

This CRUD scorecard is dominated by SQLite and JSON encoding. The framework's own hot-path micro-benchmarks — allocations per dispatch, route-match allocations and match time — are in the soak report's **Framework probes** section (`soak/report/index.html#probes`). They measure the framework, not the application.


## Where we are behind (and what to fix)

- **p95 [balanced]**: best `gofr` (91.27), zero 128.08. See `contract.md` workload notes; investigate before widening the claim.
- **p99 [balanced]**: best `axum` (132.08), zero 495.76. See `contract.md` workload notes; investigate before widening the claim.

## Reproduce

```bash
bash compare/run.sh bench
python3 compare/report.py
```

Full methodology and pinned versions: `compare/contract.md`, `results/<fw>/<fw>.version.json`, `results/<fw>-<mix>-<round>.raw.json`.

Operational evidence (leak gates, chaos recovery): the zero-soak report.
