# zero-soak report (gate)

generated: 2026-10-21 15:00:10 UTC · build: 0

**FAIL** — 13 services, 12 pass, 1 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links | TLS |
|---|---|---|---|---|---|---|---|---|
| zero-mongodb-secure | FAIL | 8080 | mongodb | no | 0/1 | — | <a href="logs/zero-mongodb-secure.log">log</a> · <a href="logs/zero-mongodb-secure.vmrss.txt">rss</a> | 🔒 |
| zero-auth | PASS | 8080 | — | no | 2/0 | 2896 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> | — |
| zero-autocrud | PASS | 8082 | — | no | 2/0 | 4600 KiB | <a href="logs/zero-autocrud.log">log</a> · <a href="logs/zero-autocrud.vmrss.txt">rss</a> | — |
| zero-basic-secure | PASS | 8080 | postgres | yes | 3/0 | 3168 KiB | <a href="logs/zero-basic-secure.log">log</a> · <a href="logs/zero-basic-secure.vmrss.txt">rss</a> | 🔒 |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 5720 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> | — |
| zero-graphql | PASS | 8080 | postgres | yes | 4/0 | 1864 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> | — |
| zero-nosql-secure | PASS | 8080 | cassandra | no | 2/0 | 8144 KiB | <a href="logs/zero-nosql-secure.log">log</a> · <a href="logs/zero-nosql-secure.vmrss.txt">rss</a> | 🔒 |
| zero-redis | PASS | 8080 | redis | yes | 3/0 | 2508 KiB | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> | — |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | 5636 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> | — |
| zero-search | PASS | 8080 | solr | no | 2/0 | 7280 KiB | <a href="logs/zero-search.log">log</a> · <a href="logs/zero-search.vmrss.txt">rss</a> | — |
| zero-sql-secure | PASS | 8080 | mysql | yes | 3/0 | 3532 KiB | <a href="logs/zero-sql-secure.log">log</a> · <a href="logs/zero-sql-secure.vmrss.txt">rss</a> | — |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 4608 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> | — |
| zero-timeseries | PASS | 8080 | influx | no | 2/0 | 1400 KiB | <a href="logs/zero-timeseries.log">log</a> · <a href="logs/zero-timeseries.vmrss.txt">rss</a> | — |

## Details

### zero-mongodb-secure (FAIL)

| Status | Check | Detail |
|---|---|---|
| FAIL | server crashed at startup (see /drone/src/soak/zero-mongodb-secure.log) |  |

**Load applied:** loader=unknown, concurrency=unknown, duration_min=1, mode=gate

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 207888 KiB |
| Overall RSS | 210784 KiB |
| dRss (growth) | 2896 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-autocrud (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 258632 KiB |
| Overall RSS | 263232 KiB |
| dRss (growth) | 4600 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-basic-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214984 KiB |
| Overall RSS | 218152 KiB |
| dRss (growth) | 3168 KiB |

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
| Baseline | 248260 KiB |
| Overall RSS | 253980 KiB |
| dRss (growth) | 5720 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 221716 KiB |
| Overall RSS | 223580 KiB |
| dRss (growth) | 1864 KiB |

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
| Baseline | 206508 KiB |
| Overall RSS | 214652 KiB |
| dRss (growth) | 8144 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-redis (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 208564 KiB |
| Overall RSS | 211072 KiB |
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
| Baseline | 208684 KiB |
| Overall RSS | 214320 KiB |
| dRss (growth) | 5636 KiB |

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
| Baseline | 208340 KiB |
| Overall RSS | 215620 KiB |
| dRss (growth) | 7280 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-sql-secure (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 209868 KiB |
| Overall RSS | 213400 KiB |
| dRss (growth) | 3532 KiB |

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
| Baseline | 213748 KiB |
| Overall RSS | 218356 KiB |
| dRss (growth) | 4608 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-timeseries (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 209272 KiB |
| Overall RSS | 210672 KiB |
| dRss (growth) | 1400 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate
