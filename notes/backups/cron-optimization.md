# Cloudflare Cron optimization

Inkstone's two original schedules (`0 * * * *`, `15,45 * * * *`) both invoke the same `scheduled` handler, which runs database initialization, scheduled backups, attachment cleanup, expired OAuth/MCP/operational data cleanup, AI indexing, and FTS queue draining. Since no cron-based branch exists, the schedules were merged into hourly `0 * * * *` to retain all features while reducing executions.

This note records the source-of-truth config change and should be committed with the code change.
