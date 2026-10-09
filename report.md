# zero-soak report (gate)

generated: 2026-10-09 03:45:13 UTC · commit: cb6ef0d3df593ba084a75148233ba7747ba12ae6 · build: 21

**PASS** — 6 services, 6 pass, 0 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links |
|---|---|---|---|---|---|---|---|
| zero-auth | PASS | 8080 | — | no | 2/0 | 5640 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> |
| zero-basic | PASS | 8080 | postgres | yes | 3/0 | 3160 KiB | <a href="logs/zero-basic.log">log</a> · <a href="logs/zero-basic.vmrss.txt">rss</a> |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 19744 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> |
| zero-redis | PASS | 8080 | redis | yes | 3/0 | 4812 KiB | <a href="logs/zero-redis.log">log</a> · <a href="logs/zero-redis.vmrss.txt">rss</a> |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | 6940 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> |
| zero-sqlite | PASS | 8081 | — | no | 2/0 | 9404 KiB | <a href="logs/zero-sqlite.log">log</a> · <a href="logs/zero-sqlite.vmrss.txt">rss</a> |

## Details

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 225664 KiB |
| Overall RSS | 231304 KiB |
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
| Baseline | 214700 KiB |
| Overall RSS | 217860 KiB |
| dRss (growth) | 3160 KiB |

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
| Baseline | 261812 KiB |
| Overall RSS | 281556 KiB |
| dRss (growth) | 19744 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate

### zero-redis (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 227700 KiB |
| Overall RSS | 232512 KiB |
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
| Overall RSS | 232612 KiB |
| dRss (growth) | 6940 KiB |

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
| Baseline | 229124 KiB |
| Overall RSS | 238528 KiB |
| dRss (growth) | 9404 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

**Load applied:** loader=go-wrk, concurrency=5 (per route), duration_min=1, mode=gate
