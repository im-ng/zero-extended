# zero-soak report (gate)

generated: 2026-10-23 02:12:47 UTC · commit: e4c2e37fe701bb737390629782a48e2f4ab4377c · build: 3

**MISSING** — 12 services, 11 pass, 0 fail, 1 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-autocrud | MISSING | 8082 | — | no | — | — | — | — |
| zero-auth | PASS | 8080 | — | no | 2/0 | 2960 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 3/0 | 3464 KiB | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 6084 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 4/0 | 2128 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | 7832 KiB | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-redis | PASS | 8080 | redis | yes | 3/0 | 2504 KiB | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | 6568 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | 6600 KiB | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 3/0 | 3768 KiB | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 4604 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | 2500 KiB | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |

## Details

### zero-autocrud (MISSING)

| Status | Check | Detail |
|---|---|---|
| — | no checks recorded | |

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212084 KiB |
| Overall RSS | 215044 KiB |
| dRss (growth) | 2960 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-basic-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 219400 KiB |
| Overall RSS | 222864 KiB |
| dRss (growth) | 3464 KiB |

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
| Baseline | 248280 KiB |
| Overall RSS | 254364 KiB |
| dRss (growth) | 6084 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 226152 KiB |
| Overall RSS | 228280 KiB |
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
| Baseline | 213136 KiB |
| Overall RSS | 220968 KiB |
| dRss (growth) | 7832 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-redis (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 212596 KiB |
| Overall RSS | 215100 KiB |
| dRss (growth) | 2504 KiB |

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
| Baseline | 211772 KiB |
| Overall RSS | 218340 KiB |
| dRss (growth) | 6568 KiB |

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
| Baseline | 212316 KiB |
| Overall RSS | 218916 KiB |
| dRss (growth) | 6600 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-sql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 213968 KiB |
| Overall RSS | 217736 KiB |
| dRss (growth) | 3768 KiB |

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
| Baseline | 218108 KiB |
| Overall RSS | 222712 KiB |
| dRss (growth) | 4604 KiB |

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
