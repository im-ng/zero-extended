# zero-soak report (gate)

generated: 2026-11-23 01:35:44 UTC · build: 21
framework: zero @ experimental-0.17 (6e2994a8) · https://gitea.pi/ng/zero.git

**MISSING** — 4 services, 0 pass, 0 fail, 4 missing.


## Framework probes (hot-path micro-benchmark)

| Metric | Value |
|---|---|
| allocs / request | 20.00 |
| bytes / request | 13615 |
| alloc leak | 0 bytes OK |
| route-match allocs | 0 |
| route match time | 568.59 ns |

_Dispatch/routing internals — not application throughput._

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-circuitbreaker | MISSING | 9090 | zero-auth | yes | — | — | — | — |
| zero-pubsub-subscriber | MISSING | 8080 | nats | no | — | — | — | — |
| zero-ratelimit | MISSING | 8080 | postgres | yes | — | — | — | — |
| zero-redis | MISSING | 8080 | redis | yes | — | — | — | — |

## Details

### zero-circuitbreaker (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |

### zero-pubsub-subscriber (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |

### zero-ratelimit (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |

### zero-redis (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 60029.3 | 4302.1 | 55727.2 | 0 bytes OK |

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
- route match time: 568.59 ns/req
- match-time allocs: 0
