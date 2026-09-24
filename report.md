# zero-soak report (gate)

generated: 2026-09-24 04:06:30 UTC · commit: 84e91cb643e2ee627c414e2b492dde16aa7fcecf · build: 8

**PASS** — 1 services, 1 pass, 0 fail, 0 missing.

| Service | Status | Port | Backends | Chaos | Checks | RSS growth | Links |
|---|---|---|---|---|---|---|---|
| zero-auth | PASS | 8082 | — | no | 4/0 | 12 KiB | <a href="logs/zero-auth.log">log</a> · <a href="logs/zero-auth.vmrss.txt">rss</a> |

## Details

### zero-auth (PASS)

**RSS**

| Metric | Value |
|---|---|
| Baseline | 61344 KiB |
| Overall RSS | 61356 KiB |
| dRss (growth) | 12 KiB |

| Status | Check | Detail |
|---|---|---|
| PASS | health up |  |
| PASS | RSS plateau (no leak) |  |
| PASS | debug health up |  |
| PASS | no debug leaks |  |
