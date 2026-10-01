# zero-soak report (gate)

generated: 2026-10-01 05:03:31 UTC · commit: 081aca6e79aacdb9658093f4e46b7594eda37e6c · build: 12

**PASS** — 5 services, 5 pass, 0 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links |
|---|---|---|---|---|---|---|---|
| zero-auth | PASS | 8080 | — | no | 2/0 | 0 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> |
| zero-basic | PASS | 8080 | postgres | yes | 3/0 | 0 KiB | <a href="logs/zero-basic.log">log</a> · <a href="logs/zero-basic.vmrss.txt">rss</a> |
| zero-duckdb | PASS | 8083 | — | no | 2/0 | 0 KiB | <a href="logs/zero-duckdb.log">log</a> · <a href="logs/zero-duckdb.vmrss.txt">rss</a> |
| zero-graphql | PASS | 8080 | postgres | yes | 4/0 | 244 KiB | <a href="logs/zero-graphql.log">log</a> · <a href="logs/zero-graphql.vmrss.txt">rss</a> |
| zero-s3 | PASS | 8080 | rustfs | yes | 4/0 | 920 KiB | <a href="logs/zero-s3.log">log</a> · <a href="logs/zero-s3.vmrss.txt">rss</a> |

## Details

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 254000 KiB |
| Overall RSS | 254000 KiB |
| dRss (growth) | 0 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

### zero-basic (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 230280 KiB |
| Overall RSS | 230280 KiB |
| dRss (growth) | 0 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | chaos survived + recovered |  |

### zero-duckdb (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 0 KiB |
| Overall RSS | 0 KiB |
| dRss (growth) | 0 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |

### zero-graphql (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 256668 KiB |
| Overall RSS | 256912 KiB |
| dRss (growth) | 244 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | graphql query OK (200, data.users present) |  |
| PASS | chaos survived + recovered |  |

### zero-s3 (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 254148 KiB |
| Overall RSS | 255068 KiB |
| dRss (growth) | 920 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | filestore round-trip (upload+download) OK |  |
| PASS | chaos survived + recovered |  |
