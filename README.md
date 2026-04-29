# 📈 Silex PMS — Status

Public uptime + performance monitor for [Silex PMS](https://silexpms.com), powered by [Upptime](https://upptime.js.org).

GitHub Actions hits each endpoint every 5 minutes from outside our infrastructure (independent of Cloudflare). When something goes down, an issue is auto-opened and the response-time graph reflects it.

**Live status site**: [status.silexpms.com](https://status.silexpms.com) (after first workflow run + DNS).

## Endpoints monitored

- `https://pms-api.silexpms.com/health` — central API health
- `https://admin.silexpms.com` — SaaS Owner Console
- `https://loslimones.silexpms.com/login` — tenant routing canary
- `https://donachava.silexpms.com/login` — real customer routing
- `https://mirror.silexpms.com/__nginx-health` — warm-spare on Hostinger
- `https://pms-api.silexpms.com/api/replication-health` — replication lag

## Why this exists

This is the **secondary** monitoring layer. Our primary monitor (`silex-watch`) runs as a Cloudflare Worker — if CF has a global outage, it'd take down both Silex AND our own monitor, and we wouldn't know. GitHub-hosted monitoring is independent of CF.

Plus: public accountability. Customers verify our uptime themselves.

## License

MIT
