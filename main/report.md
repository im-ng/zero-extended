# zero-soak report (gate)

generated: 2026-11-23 02:11:00 UTC · build: 23
framework: zero @ experimental-0.17 (6e2994a8) · https://gitea.pi/ng/zero.git

**FAIL** — 2 services, 0 pass, 2 fail, 0 missing.


## Framework probes (hot-path micro-benchmark)

| Metric | Value |
|---|---|
| allocs / request | 20.00 |
| bytes / request | 13615 |
| alloc leak | 0 bytes OK |
| route-match allocs | 0 |
| route match time | 577.27 ns |

_Dispatch/routing internals — not application throughput._

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-circuitbreaker | FAIL | 9090 | zero-auth | yes | 3/1 | 177660 KiB | <a href="logs/zero-circuitbreaker.log">log</a> · <a href="logs/zero-circuitbreaker.vmrss.txt">rss</a> | — |
| zero-ratelimit | FAIL | 8080 | postgres | yes | 4/1 | 2736 KiB | <a href="logs/zero-ratelimit.log">log</a> · <a href="logs/zero-ratelimit.vmrss.txt">rss</a> | — |

## Details

### zero-circuitbreaker (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 34300 KiB |
| Overall RSS | 211960 KiB |
| dRss (growth) | 177660 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-auth up |  |
| PASS | health up |  |
| PASS | RSS growth (informational in fast gate) | RSS grew 177660KiB (> 32MiB and > 50%): possible leak (Debug guard pages; nightly leak phase is authoritative) |
| FAIL | circuit breaker did not engage / did not recover |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=6s

### zero-ratelimit (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 215440 KiB |
| Overall RSS | 218176 KiB |
| dRss (growth) | 2736 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| FAIL | rate limit: no 429 observed (0/40) — limiter may be disabled or limit too high |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: postgres reachable |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=3s


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 60479.0 | 4396.3 | 56082.7 | 0 bytes OK |

top call-sites (alloc-probe-fallback.json):

| site | count/req | bytes/req |
|---|---|---|
| 0x194a914 | 4.00 | 8448 |
| 0x194a0b4 | 1.00 | 3136 |
| 0x14175c7 | 1.00 | 768 |
| 0x14172f3 | 1.00 | 256 |
| 0x141812e | 1.00 | 248 |

### Route probe (literal static routes)

- routes: 1000
- registration allocs: 9
- registration bytes: 625680
- bytes/route: 625.7
- route match time: 577.27 ns/req
- match-time allocs: 0
