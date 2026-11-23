# zero-soak report (gate)

generated: 2026-11-23 02:59:09 UTC · build: 25
framework: zero @ experimental-0.17 (6e2994a8) · https://gitea.pi/ng/zero.git

**FAIL** — 2 services, 1 pass, 1 fail, 0 missing.


## Framework probes (hot-path micro-benchmark)

| Metric | Value |
|---|---|
| allocs / request | 20.00 |
| bytes / request | 13615 |
| alloc leak | 0 bytes OK |
| route-match allocs | 0 |
| route match time | 572.59 ns |

_Dispatch/routing internals — not application throughput._

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-circuitbreaker | FAIL | 9090 | zero-auth | yes | 3/1 | 4700 KiB | <a href="logs/zero-circuitbreaker.log">log</a> · <a href="logs/zero-circuitbreaker.vmrss.txt">rss</a> | — |
| zero-ratelimit | PASS | 8080 | postgres | yes | 5/0 | 2736 KiB | <a href="logs/zero-ratelimit.log">log</a> · <a href="logs/zero-ratelimit.vmrss.txt">rss</a> | — |

## Details

### zero-circuitbreaker (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214000 KiB |
| Overall RSS | 218700 KiB |
| dRss (growth) | 4700 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-auth up |  |
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| FAIL | circuit breaker did not engage / did not recover |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=6s

### zero-ratelimit (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 215820 KiB |
| Overall RSS | 218556 KiB |
| dRss (growth) | 2736 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | rate limit: server returned 429 (30/40 requests rejected) |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: postgres reachable |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=3s


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 59324.0 | 4201.1 | 55122.9 | 0 bytes OK |

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
- route match time: 572.59 ns/req
- match-time allocs: 0
