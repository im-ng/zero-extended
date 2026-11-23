# zero-soak report (gate)

generated: 2026-11-23 01:48:13 UTC · build: 22
framework: zero @ experimental-0.17 (6e2994a8) · https://gitea.pi/ng/zero.git

**FAIL** — 4 services, 1 pass, 3 fail, 0 missing.


## Framework probes (hot-path micro-benchmark)

| Metric | Value |
|---|---|
| allocs / request | 20.00 |
| bytes / request | 13615 |
| alloc leak | 0 bytes OK |
| route-match allocs | 0 |
| route match time | 550.30 ns |

_Dispatch/routing internals — not application throughput._

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-circuitbreaker | FAIL | 9090 | zero-auth | yes | 3/1 | 177660 KiB | <a href="logs/zero-circuitbreaker.log">log</a> · <a href="logs/zero-circuitbreaker.vmrss.txt">rss</a> | — |
| zero-ratelimit | FAIL | 8080 | postgres | yes | 4/1 | 2740 KiB | <a href="logs/zero-ratelimit.log">log</a> · <a href="logs/zero-ratelimit.vmrss.txt">rss</a> | — |
| zero-redis | FAIL | 8080 | redis | yes | 0/1 | — | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-pubsub-subscriber | PASS | 8080 | nats | no | 3/0 | 275352 KiB | <a href="logs/zero-pubsub-subscriber.log">log</a> · <a href="logs/zero-pubsub-subscriber.vmrss.txt">rss</a> | — |

## Details

### zero-circuitbreaker (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 34232 KiB |
| Overall RSS | 211892 KiB |
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
| Baseline | 215968 KiB |
| Overall RSS | 218708 KiB |
| dRss (growth) | 2740 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| FAIL | rate limit: no 429 observed (0/40) — limiter may be disabled or limit too high |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: postgres reachable |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-redis (FAIL)

| Status | Check | Detail |
|---|---|---|
| FAIL | server crashed at startup (see /drone/src/soak/zero-redis.log) |  |

**Load applied:** loader=unknown, concurrency=unknown, duration_min=1, mode=gate, chaos kill-window=3s

### zero-pubsub-subscriber (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 33232 KiB |
| Overall RSS | 308584 KiB |
| dRss (growth) | 275352 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-pubsub-publisher up |  |
| PASS | health up |  |
| PASS | RSS growth (informational in fast gate) | RSS grew 275352KiB (> 32MiB and > 50%): possible leak (Debug guard pages; nightly leak phase is authoritative) |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 59188.0 | 4121.3 | 55066.6 | 0 bytes OK |

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
- route match time: 550.30 ns/req
- match-time allocs: 0
