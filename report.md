# zero-soak report (gate)

generated: 2026-10-24 03:24:25 UTC · commit: 2d57ffeadfe7467f96f369dc0d013e2cc2dd174d · build: 5

**FAIL** — 14 services, 12 pass, 2 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-autocrud | FAIL | 8082 | — | no | 1/1 | — | <a href="logs/zero-autocrud.log">log</a> · <a href="logs/zero-autocrud.vmrss.txt">rss</a> | — |
| zero-pubsub-subscriber | FAIL | 8080 | nats | no | 2/1 | — | <a href="logs/zero-pubsub-subscriber.log">log</a> · <a href="logs/zero-pubsub-subscriber.vmrss.txt">rss</a> | — |
| zero-auth | PASS | 8080 | — | no | 2/0 | — | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 3/0 | — | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | — | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 4/0 | — | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | — | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-redis | PASS | 8080 | redis | yes | 3/0 | — | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | — | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | — | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 3/0 | — | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | — | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | — | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |
| zero-ws-client | PASS | 8080 | — | no | 2/0 | — | <a href="logs/zero-ws-client.log">log</a> · <a href="logs/zero-ws-client.vmrss.txt">rss</a> | 🔒 |

## Details

### zero-autocrud (FAIL)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| FAIL | RSS leak signal | RSS grew 69436KiB (> 8MiB and > 15%): possible leak |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-pubsub-subscriber (FAIL)

| Status | Check | Detail |
|---|---|---|
| PASS | dep zero-pubsub-publisher up |  |
| PASS | health up |  |
| FAIL | RSS leak signal | RSS grew 299816KiB (> 8MiB and > 15%): possible leak |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-auth (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-basic-secure (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=2s

### zero-duckdb (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-graphql (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | graphql query OK (200, data.users present) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=graphql POST loop, concurrency=1 (sequential), duration_min=1, mode=gate, chaos kill-window=2s

### zero-nosql-secure (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-redis (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=2s

### zero-s3 (PASS)

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | filestore round-trip (upload+download) OK |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=filestore (upload→download→delete), concurrency=8, duration_min=1, mode=gate, chaos kill-window=2s

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

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=2s

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
