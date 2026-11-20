# zero-soak report (gate)

generated: 2026-11-20 15:07:24 UTC · build: 16
framework: zero @ experimental-0.17 (6e2994a8) · https://gitea.pi/ng/zero.git

**FAIL** — 16 services, 10 pass, 6 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-basic-secure | FAIL | 8080 | postgres | yes | 2/1 | — | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-circuitbreaker | FAIL | 9090 | zero-auth | yes | 3/1 | — | <a href="logs/zero-circuitbreaker.log">log</a> · <a href="logs/zero-circuitbreaker.vmrss.txt">rss</a> | — |
| zero-graphql | FAIL | 8080 | postgres | yes | 0/2 | — | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-pubsub-subscriber | FAIL | 8080 | nats | no | 2/1 | — | <a href="logs/zero-pubsub-subscriber.log">log</a> · <a href="logs/zero-pubsub-subscriber.vmrss.txt">rss</a> | — |
| zero-ratelimit | FAIL | 8080 | postgres | yes | 0/2 | — | <a href="logs/zero-ratelimit.log">log</a> · <a href="logs/zero-ratelimit.vmrss.txt">rss</a> | — |
| zero-redis | FAIL | 8080 | redis | yes | 0/1 | — | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-auth | PASS | 8080 | — | no | 2/0 | — | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-autocrud | PASS | 8082 | — | no | 2/0 | — | <a href="logs/zero-autocrud.log">log</a> · <a href="logs/zero-autocrud.vmrss.txt">rss</a> | — |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | — | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | — | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | — | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | — | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 3/0 | — | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | — | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | — | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |
| zero-ws-client | PASS | 8080 | — | no | 2/0 | — | <a href="logs/zero-ws-client.log">log</a> · <a href="logs/zero-ws-client.vmrss.txt">rss</a> | 🔒 |

## Details

### zero-basic-secure (FAIL)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| FAIL | RSS leak signal | RSS grew 60408KiB (> 16MiB and > 25%): possible leak |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=10s

### zero-circuitbreaker (FAIL)

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-auth up |  |
| PASS | health up |  |
| FAIL | RSS leak signal | RSS grew 186440KiB (> 16MiB and > 25%): possible leak |
| PASS | circuit breaker: degraded gracefully under outage + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=10s

### zero-graphql (FAIL)

| Status | Check | Detail |
|---|---|---|
| FAIL | backend postgres not ready |  |
| FAIL | health never came up |  |

**Load applied:** loader=unknown, concurrency=unknown, duration_min=1, mode=gate, chaos kill-window=10s

### zero-pubsub-subscriber (FAIL)

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-pubsub-publisher up |  |
| PASS | health up |  |
| FAIL | RSS leak signal | RSS grew 275796KiB (> 16MiB and > 25%): possible leak |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-ratelimit (FAIL)

| Status | Check | Detail |
|---|---|---|
| FAIL | backend postgres not ready |  |
| FAIL | health never came up |  |

**Load applied:** loader=unknown, concurrency=unknown, duration_min=1, mode=gate, chaos kill-window=10s

### zero-redis (FAIL)

| Status | Check | Detail |
|---|---|---|
| FAIL | health never came up |  |

**Load applied:** loader=unknown, concurrency=unknown, duration_min=1, mode=gate, chaos kill-window=10s

### zero-auth (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-autocrud (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-duckdb (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-nosql-secure (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-s3 (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | filestore round-trip (upload+download) OK |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=filestore (upload→download→delete), concurrency=8, duration_min=1, mode=gate, chaos kill-window=10s

### zero-search (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-sql-secure (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=10s

### zero-sqlite (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-timeseries (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-ws-client (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate


## Framework probes

### Allocation probe (GET /ping → pong)

| backing | allocs/req | bytes/req | latency/req ns | alloc-time/req ns | dispatch-only/req ns | leaked |
|---|---|---|---|---|---|---|
| fallback | 20.00 | 13615 | 61029.8 | 4320.8 | 56709.0 | 0 bytes OK |

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
- route match time: 549.17 ns/req
- match-time allocs: 0
