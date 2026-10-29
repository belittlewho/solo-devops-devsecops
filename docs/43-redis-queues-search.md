# Part 43 — Redis, Message Queues & Search

---

## Redis persistence

| Mode | Use |
|------|-----|
| RDB snapshots | Periodic point-in-time |
| AOF | Durability every write |
| Neither | Pure cache only |

```conf
maxmemory 256mb
maxmemory-policy allkeys-lru
```

Monitor `used_memory`, evicted keys.

---

## RabbitMQ (self-host)

```bash
docker run -d --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
```

Queues, exchanges, DLQ for poison messages.

---

## AWS SQS pattern

Visibility timeout > max processing time; dead-letter queue after N receives.

---

## Kafka (intro)

Topics, partitions, consumer groups — use when high throughput event log needed. Managed: MSK, Confluent Cloud. Overkill for solo cron — start SQS/RabbitMQ.

---

## OpenSearch / Elasticsearch ops

Cluster health `green`; disk watermarks; index lifecycle (hot → warm → delete). Prefer managed OpenSearch until cluster ops skill exists.

Next: [Part 44 — Observability lab](44-observability-stack-lab.md)
