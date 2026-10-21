# zero-soak report (gate)

generated: 2026-10-21 15:34:38 UTC · build: 0

**PASS** — 12 services, 12 pass, 0 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-auth | PASS | 8080 | — | no | 2/0 | 2900 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-autocrud | PASS | 8082 | — | no | 2/0 | 4604 KiB | <a href="logs/zero-autocrud.log">log</a> · <a href="logs/zero-autocrud.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 3/0 | 3140 KiB | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 5984 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 4/0 | 1728 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | 7708 KiB | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-redis | PASS | 8080 | redis | yes | 3/0 | 2508 KiB | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | 6736 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | 7320 KiB | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 3/0 | 3676 KiB | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 4624 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | 2536 KiB | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |

## Details

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 206092 KiB |
| Overall RSS | 208992 KiB |
| dRss (growth) | 2900 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-autocrud (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 257344 KiB |
| Overall RSS | 261948 KiB |
| dRss (growth) | 4604 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-basic-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212704 KiB |
| Overall RSS | 215844 KiB |
| dRss (growth) | 3140 KiB |

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
| Baseline | 245824 KiB |
| Overall RSS | 251808 KiB |
| dRss (growth) | 5984 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 220596 KiB |
| Overall RSS | 222324 KiB |
| dRss (growth) | 1728 KiB |

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
| Baseline | 207216 KiB |
| Overall RSS | 214924 KiB |
| dRss (growth) | 7708 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-redis (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 205704 KiB |
| Overall RSS | 208212 KiB |
| dRss (growth) | 2508 KiB |

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
| Baseline | 205820 KiB |
| Overall RSS | 212556 KiB |
| dRss (growth) | 6736 KiB |

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
| Baseline | 206532 KiB |
| Overall RSS | 213852 KiB |
| dRss (growth) | 7320 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-sql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 208596 KiB |
| Overall RSS | 212272 KiB |
| dRss (growth) | 3676 KiB |

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
| Baseline | 211836 KiB |
| Overall RSS | 216460 KiB |
| dRss (growth) | 4624 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-timeseries (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 207344 KiB |
| Overall RSS | 209880 KiB |
| dRss (growth) | 2536 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate
