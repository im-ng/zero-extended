# zero-soak report (gate)

generated: 2026-11-23 05:11:21 UTC · build: 29
framework: zero @ experimental-0.17 (db8e20d1) · https://gitea.pi/ng/zero.git

**FAIL** — 15 services, 13 pass, 2 fail, 0 missing.


## Framework probes (hot-path micro-benchmark)

| Metric | Value |
|---|---|
| allocs / request | 20.00 |
| bytes / request | 13615 |
| alloc leak | 0 bytes OK |
| route-match allocs | 0 |
| route match time | 655.40 ns |

_Dispatch/routing internals — not application throughput._

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-circuitbreaker | FAIL | 9090 | zero-auth | yes | 3/2 | 5572 KiB | <a href="logs/zero-circuitbreaker.log">log</a> · <a href="logs/zero-circuitbreaker.vmrss.txt">rss</a> | — |
| zero-s3 | FAIL | 8080 | rustfs | yes | 3/2 | 7588 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-auth | PASS | 8080 | — | no | 2/0 | 3008 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-autocrud | PASS | 8082 | — | no | 2/0 | 4972 KiB | <a href="logs/zero-autocrud.log">log</a> · <a href="logs/zero-autocrud.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 4/0 | 55636 KiB | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 6772 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 5/0 | 57400 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | 2428 KiB | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-pubsub-subscriber | PASS | 8080 | nats | no | 3/0 | 4624 KiB | <a href="logs/zero-pubsub-subscriber.log">log</a> · <a href="logs/zero-pubsub-subscriber.vmrss.txt">rss</a> | — |
| zero-ratelimit | PASS | 8080 | postgres | yes | 5/0 | 2696 KiB | <a href="logs/zero-ratelimit.log">log</a> · <a href="logs/zero-ratelimit.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | 7848 KiB | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 4/0 | 4320 KiB | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 2708 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | 2624 KiB | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |
| zero-ws-client | PASS | 8080 | — | no | 2/0 | 88 KiB | <a href="logs/zero-ws-client.log">log</a> · <a href="logs/zero-ws-client.vmrss.txt">rss</a> | 🔒 |

## Details

### zero-circuitbreaker (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 221876 KiB |
| Overall RSS | 227448 KiB |
| dRss (growth) | 5572 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-auth up |  |
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| FAIL | chaos baseline: data route /keys is HTTP 500 (not 200) |  |
| FAIL | circuit breaker did not engage / did not recover |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=6s

### zero-s3 (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214376 KiB |
| Overall RSS | 221964 KiB |
| dRss (growth) | 7588 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| FAIL | filestore upload failed | resp=[] |
| FAIL | chaos caused failure |  |
| PASS | chaos cleanup: rustfs reachable |  |

**Load applied:** loader=filestore (upload→download→delete), concurrency=8, duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212444 KiB |
| Overall RSS | 215452 KiB |
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
| Baseline | 265916 KiB |
| Overall RSS | 270888 KiB |
| dRss (growth) | 4972 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-basic-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 167312 KiB |
| Overall RSS | 222948 KiB |
| dRss (growth) | 55636 KiB |

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
| Baseline | 250268 KiB |
| Overall RSS | 257040 KiB |
| dRss (growth) | 6772 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 173652 KiB |
| Overall RSS | 231052 KiB |
| dRss (growth) | 57400 KiB |

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
| Baseline | 216012 KiB |
| Overall RSS | 218440 KiB |
| dRss (growth) | 2428 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-pubsub-subscriber (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 308992 KiB |
| Overall RSS | 313616 KiB |
| dRss (growth) | 4624 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-pubsub-publisher up |  |
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-ratelimit (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 227248 KiB |
| Overall RSS | 229944 KiB |
| dRss (growth) | 2696 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | rate limit: server returned 429 (30/40 requests rejected) |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: postgres reachable |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-search (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 221232 KiB |
| Overall RSS | 229080 KiB |
| dRss (growth) | 7848 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-sql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214724 KiB |
| Overall RSS | 219044 KiB |
| dRss (growth) | 4320 KiB |

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
| Baseline | 218884 KiB |
| Overall RSS | 221592 KiB |
| dRss (growth) | 2708 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-timeseries (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 222876 KiB |
| Overall RSS | 225500 KiB |
| dRss (growth) | 2624 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-ws-client (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 227456 KiB |
| Overall RSS | 227544 KiB |
| dRss (growth) | 88 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 60382.9 | 4272.4 | 56110.6 | 0 bytes OK |

top call-sites (alloc-probe-fallback.json):

| site | count/req | bytes/req |
|---|---|---|
| 0x194db94 | 4.00 | 8448 |
| 0x194d334 | 1.00 | 3136 |
| 0x14185c7 | 1.00 | 768 |
| 0x14182f3 | 1.00 | 256 |
| 0x141912e | 1.00 | 248 |

### Route probe (literal static routes)

- routes: 1000
- registration allocs: 9
- registration bytes: 625680
- bytes/route: 625.7
- route match time: 655.40 ns/req
- match-time allocs: 0
