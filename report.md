# zero-soak report (gate)

generated: 2026-10-08 05:17:07 UTC · commit: cb6ef0d3df593ba084a75148233ba7747ba12ae6 · build: 20

**FAIL** — 6 services, 5 pass, 1 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links |
|---|---|---|---|---|---|---|---|
| zero-duckdb | FAIL | 8083 | — | no | 0/1 | — | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> |
| zero-auth | PASS | 8080 | — | no | 2/0 | 5640 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> |
| zero-basic | PASS | 8080 | postgres | yes | 3/0 | 2928 KiB | <a href="logs/zero-basic.log">log</a> · <a href="logs/zero-basic.vmrss.txt">rss</a> |
| zero-redis | PASS | 8080 | redis | yes | 3/0 | 4812 KiB | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | 5688 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 4652 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> |

## Details

### zero-duckdb (FAIL)

| Status | Check | Detail |
|---|---|---|
| FAIL | health never came up |  |

**Load applied:** loader=unknown, concurrency=unknown, duration_min=1, mode=gate

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 225576 KiB |
| Overall RSS | 231216 KiB |
| dRss (growth) | 5640 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-basic (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 214792 KiB |
| Overall RSS | 217720 KiB |
| dRss (growth) | 2928 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate, chaos kill-window=2s

### zero-redis (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 225704 KiB |
| Overall RSS | 230516 KiB |
| dRss (growth) | 4812 KiB |

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
| Baseline | 225672 KiB |
| Overall RSS | 231360 KiB |
| dRss (growth) | 5688 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | filestore round-trip (upload+download) OK |  |
| PASS | chaos survived + recovered |  |

**Load applied:** loader=filestore (upload→download→delete), concurrency=8, duration_min=1, mode=gate, chaos kill-window=2s

### zero-sqlite (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 229300 KiB |
| Overall RSS | 233952 KiB |
| dRss (growth) | 4652 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate
