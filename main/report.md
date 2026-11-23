# zero-soak report (gate)

generated: 2026-11-23 04:27:28 UTC · build: 28
framework: zero @ experimental-0.17 (011276f2) · https://gitea.pi/ng/zero.git

**FAIL** — 15 services, 13 pass, 1 fail, 1 missing.


## Framework probes (hot-path micro-benchmark)

| Metric | Value |
|---|---|
| allocs / request | 20.00 |
| bytes / request | 13615 |
| alloc leak | 0 bytes OK |
| route-match allocs | 0 |
| route match time | 568.26 ns |

_Dispatch/routing internals — not application throughput._

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-s3 | FAIL | 8080 | rustfs | yes | 4/1 | 8184 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-circuitbreaker | MISSING | 9090 | zero-auth | yes | — | — | — | — |
| zero-auth | PASS | 8080 | — | no | 2/0 | 3008 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-autocrud | PASS | 8082 | — | no | 2/0 | 4964 KiB | <a href="logs/zero-autocrud.log">log</a> · <a href="logs/zero-autocrud.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 4/0 | 3872 KiB | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 6920 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 5/0 | 2328 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | 2476 KiB | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-pubsub-subscriber | PASS | 8080 | nats | no | 3/0 | 4632 KiB | <a href="logs/zero-pubsub-subscriber.log">log</a> · <a href="logs/zero-pubsub-subscriber.vmrss.txt">rss</a> | — |
| zero-ratelimit | PASS | 8080 | postgres | yes | 5/0 | 2684 KiB | <a href="logs/zero-ratelimit.log">log</a> · <a href="logs/zero-ratelimit.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | 6568 KiB | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 4/0 | 4276 KiB | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 2708 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | 1264 KiB | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |
| zero-ws-client | PASS | 8080 | — | no | 2/0 | 92 KiB | <a href="logs/zero-ws-client.log">log</a> · <a href="logs/zero-ws-client.vmrss.txt">rss</a> | 🔒 |

## Details

### zero-s3 (FAIL)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212372 KiB |
| Overall RSS | 220556 KiB |
| dRss (growth) | 8184 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| FAIL | filestore upload failed | resp=[] |
| PASS | chaos survived + recovered |  |
| PASS | chaos cleanup: rustfs reachable |  |

**Load applied:** loader=filestore (upload→download→delete), concurrency=8, duration_min=0.25, mode=gate, chaos kill-window=3s

### zero-circuitbreaker (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212428 KiB |
| Overall RSS | 215436 KiB |
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
| Baseline | 265924 KiB |
| Overall RSS | 270888 KiB |
| dRss (growth) | 4964 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-basic-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 220476 KiB |
| Overall RSS | 224348 KiB |
| dRss (growth) | 3872 KiB |

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
| Baseline | 250068 KiB |
| Overall RSS | 256988 KiB |
| dRss (growth) | 6920 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 228848 KiB |
| Overall RSS | 231176 KiB |
| dRss (growth) | 2328 KiB |

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
| Baseline | 214060 KiB |
| Overall RSS | 216536 KiB |
| dRss (growth) | 2476 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-pubsub-subscriber (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 312632 KiB |
| Overall RSS | 317264 KiB |
| dRss (growth) | 4632 KiB |

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
| Baseline | 227408 KiB |
| Overall RSS | 230092 KiB |
| dRss (growth) | 2684 KiB |

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
| Baseline | 221344 KiB |
| Overall RSS | 227912 KiB |
| dRss (growth) | 6568 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate

### zero-sql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214756 KiB |
| Overall RSS | 219032 KiB |
| dRss (growth) | 4276 KiB |

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
| Baseline | 218508 KiB |
| Overall RSS | 221216 KiB |
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
| Baseline | 222888 KiB |
| Overall RSS | 224152 KiB |
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
| Baseline | 227680 KiB |
| Overall RSS | 227772 KiB |
| dRss (growth) | 92 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=0.25, mode=gate


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 60803.0 | 4232.9 | 56570.1 | 0 bytes OK |

top call-sites (alloc-probe-fallback.json):

| site | count/req | bytes/req |
|---|---|---|
| 0x194d664 | 4.00 | 8448 |
| 0x194ce04 | 1.00 | 3136 |
| 0x14185c7 | 1.00 | 768 |
| 0x14182f3 | 1.00 | 256 |
| 0x141912e | 1.00 | 248 |

### Route probe (literal static routes)

- routes: 1000
- registration allocs: 9
- registration bytes: 625680
- bytes/route: 625.7
- route match time: 568.26 ns/req
- match-time allocs: 0
