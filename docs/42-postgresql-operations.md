# Part 42 — PostgreSQL Operations

---

## Roles & least privilege

```sql
CREATE ROLE app_login LOGIN PASSWORD '...';
GRANT CONNECT ON DATABASE myapp TO app_login;
GRANT USAGE ON SCHEMA public TO app_login;
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO app_login;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO app_login;
```

Migrations user separate from app user.

---

## Extensions

```sql
CREATE EXTENSION IF NOT EXISTS "pgcrypto";
CREATE EXTENSION IF NOT EXISTS "citext";
```

Document in runbook; version pin in staging first.

---

## Vacuum & bloat

```sql
SELECT relname, last_vacuum, last_autovacuum FROM pg_stat_user_tables;
```

Tune `autovacuum` on write-heavy tables.

---

## Backups: pg_dump

```bash
pg_dump -Fc -h localhost -U postgres myapp > myapp_$(date +%F).dump
```

Cron + encrypt + upload offsite (Part 19).

---

## PITR (WAL archiving)

`postgresql.conf`:

```
archive_mode = on
archive_command = 'aws s3 cp %p s3://bucket/wal/%f'
```

Base backup + continuous WAL → point-in-time restore.

---

## Replication / failover

Primary + standby streaming replication; Patroni or managed RDS Multi-AZ for auto failover.

Read replicas for analytics — lag monitoring.

---

## Connection pooling (PgBouncer)

```ini
[databases]
myapp = host=127.0.0.1 port=5432 dbname=myapp

[pgbouncer]
pool_mode = transaction
max_client_conn = 200
default_pool_size = 20
```

App connects to 6432, not direct Postgres storm.

Next: [Part 43 — Redis & messaging](43-redis-queues-search.md)
