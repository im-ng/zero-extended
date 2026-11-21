# zero-soak report (gate)

generated: 2026-11-21 04:23:19 UTC · build: 20
framework: zero @ experimental-0.17 (6e2994a8) · https://gitea.pi/ng/zero.git

**FAIL** — 16 services, 12 pass, 4 fail, 0 missing.


## Framework probes (hot-path micro-benchmark)

| Metric | Value |
|---|---|
| allocs / request | 20.00 |
| bytes / request | 13615 |
| alloc leak | 0 bytes OK |
| route-match allocs | 0 |
| route match time | 567.59 ns |

_Dispatch/routing internals — not application throughput._

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-circuitbreaker | FAIL | 9090 | zero-auth | yes | 2/2 | 177720 KiB ⚠ | <a href="logs/zero-circuitbreaker.log">log</a> · <a href="logs/zero-circuitbreaker.vmrss.txt">rss</a> | — |
| zero-pubsub-subscriber | FAIL | 8080 | nats | no | 2/1 | 275584 KiB ⚠ | <a href="logs/zero-pubsub-subscriber.log">log</a> · <a href="logs/zero-pubsub-subscriber.vmrss.txt">rss</a> | — |
| zero-ratelimit | FAIL | 8080 | postgres | yes | 4/1 | 1212 KiB | <a href="logs/zero-ratelimit.log">log</a> · <a href="logs/zero-ratelimit.vmrss.txt">rss</a> | — |
| zero-redis | FAIL | 8080 | redis | yes | 0/1 | — | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-auth | PASS | 8080 | — | no | 2/0 | 3008 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-autocrud | PASS | 8082 | — | no | 2/0 | 4968 KiB | <a href="logs/zero-autocrud.log">log</a> · <a href="logs/zero-autocrud.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 4/0 | 55640 KiB | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 6596 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 5/0 | 2276 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | 2548 KiB | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-s3 | PASS | 8080 | rustfs | yes | 5/0 | 8512 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | 7752 KiB | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 4/0 | 4312 KiB | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 5028 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | 1264 KiB | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |
| zero-ws-client | PASS | 8080 | — | no | 2/0 | 56 KiB | <a href="logs/zero-ws-client.log">log</a> · <a href="logs/zero-ws-client.vmrss.txt">rss</a> | 🔒 |

## Details

### zero-circuitbreaker (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 34224 KiB |
| Overall RSS | 211944 KiB |
| dRss (growth) | 177720 KiB ⚠ leak |

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-auth up |  |
| PASS | health up |  |
| FAIL | RSS leak signal | RSS grew 177720KiB (> 32MiB and > 50%): possible leak |
| FAIL | circuit breaker did not engage / did not recover |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=6s

### zero-pubsub-subscriber (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 33172 KiB |
| Overall RSS | 308756 KiB |
| dRss (growth) | 275584 KiB ⚠ leak |

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-pubsub-publisher up |  |
| PASS | health up |  |
| FAIL | RSS leak signal | RSS grew 275584KiB (> 32MiB and > 50%): possible leak |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-ratelimit (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 217644 KiB |
| Overall RSS | 218856 KiB |
| dRss (growth) | 1212 KiB |

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
| FAIL | health never came up |  |

**Load applied:** loader=unknown, concurrency=unknown, duration_min=1, mode=gate, chaos kill-window=3s

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214644 KiB |
| Overall RSS | 217652 KiB |
| dRss (growth) | 3008 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-autocrud (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 218048 KiB |
| Overall RSS | 223016 KiB |
| dRss (growth) | 4968 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-basic-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 167340 KiB |
| Overall RSS | 222980 KiB |
| dRss (growth) | 55640 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: postgres reachable |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-duckdb (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 250340 KiB |
| Overall RSS | 256936 KiB |
| dRss (growth) | 6596 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 215488 KiB |
| Overall RSS | 217764 KiB |
| dRss (growth) | 2276 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | graphql query OK (200, data.users present) |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: postgres reachable |  |

**Load applied:** loader=graphql POST loop, concurrency=1 (sequential), duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-nosql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 227572 KiB |
| Overall RSS | 230120 KiB |
| dRss (growth) | 2548 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-s3 (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212604 KiB |
| Overall RSS | 221116 KiB |
| dRss (growth) | 8512 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | filestore round-trip (upload+download) OK |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: rustfs reachable |  |

**Load applied:** loader=filestore (upload→download→delete), concurrency=8, duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-search (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 221332 KiB |
| Overall RSS | 229084 KiB |
| dRss (growth) | 7752 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-sql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 228080 KiB |
| Overall RSS | 232392 KiB |
| dRss (growth) | 4312 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: mysql reachable |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-sqlite (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 218876 KiB |
| Overall RSS | 223904 KiB |
| dRss (growth) | 5028 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-timeseries (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 223072 KiB |
| Overall RSS | 224336 KiB |
| dRss (growth) | 1264 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-ws-client (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 219172 KiB |
| Overall RSS | 219228 KiB |
| dRss (growth) | 56 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 62353.5 | 4413.4 | 57940.0 | 0 bytes OK |

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
- route match time: 567.59 ns/req
- match-time allocs: 0
