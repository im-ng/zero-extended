# zero-soak report (gate)

generated: 2026-10-24 02:31:19 UTC · commit: 6e8f860ab91b5023c37031c1940d8557d8f3b9d6 · build: 4

**MISSING** — 14 services, 12 pass, 0 fail, 2 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-autocrud | MISSING | 8082 | — | no | — | — | — | — |
| zero-pubsub-subscriber | MISSING | 8080 | nats | no | — | — | — | — |
| zero-auth | PASS | 8080 | — | no | 2/0 | 2956 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 3/0 | 10508 KiB | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 10724 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 4/0 | 2128 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | 7788 KiB | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-redis | PASS | 8080 | redis | yes | 3/0 | 1208 KiB | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | 6968 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | 7444 KiB | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 3/0 | 3836 KiB | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 4612 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | 2500 KiB | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |
| zero-ws-client | PASS | 8080 | — | no | 2/0 | 64 KiB | <a href="logs/zero-ws-client.log">log</a> · <a href="logs/zero-ws-client.vmrss.txt">rss</a> | 🔒 |

## Details

### zero-autocrud (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |

### zero-pubsub-subscriber (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 211888 KiB |
| Overall RSS | 214844 KiB |
| dRss (growth) | 2956 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-basic-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212300 KiB |
| Overall RSS | 222808 KiB |
| dRss (growth) | 10508 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=2s

### zero-duckdb (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 248212 KiB |
| Overall RSS | 258936 KiB |
| dRss (growth) | 10724 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 226096 KiB |
| Overall RSS | 228224 KiB |
| dRss (growth) | 2128 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | graphql query OK (200, data.users present) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=graphql POST loop, concurrency=1 (sequential), duration_min=1, mode=gate, chaos kill-window=2s

### zero-nosql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 213532 KiB |
| Overall RSS | 221320 KiB |
| dRss (growth) | 7788 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-redis (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212356 KiB |
| Overall RSS | 213564 KiB |
| dRss (growth) | 1208 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=2s

### zero-s3 (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 211452 KiB |
| Overall RSS | 218420 KiB |
| dRss (growth) | 6968 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | filestore round-trip (upload+download) OK |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=filestore (upload→download→delete), concurrency=8, duration_min=1, mode=gate, chaos kill-window=2s

### zero-search (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212308 KiB |
| Overall RSS | 219752 KiB |
| dRss (growth) | 7444 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-sql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214280 KiB |
| Overall RSS | 218116 KiB |
| dRss (growth) | 3836 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=2s

### zero-sqlite (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 218072 KiB |
| Overall RSS | 222684 KiB |
| dRss (growth) | 4612 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-timeseries (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 213500 KiB |
| Overall RSS | 216000 KiB |
| dRss (growth) | 2500 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-ws-client (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 225816 KiB |
| Overall RSS | 225880 KiB |
| dRss (growth) | 64 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate
