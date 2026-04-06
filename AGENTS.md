# AGENTS.md

## Purpose
Public self-hosted deployment template for ClickHouse analytics database.

## Repository Role
- Category: `*-self-hosted` (public GitHub repository).
- Related local stack: `../clickhouse-docker`.
- Main entrypoint: `docker-compose.yml`.

## Stack Summary
- Service: `clickhouse`.
- Exposed ports: `8123` (HTTP), `9000` (native TCP).
- External network: `shared_network`.

## Data and Config
- Persistent data: `./data/clickhouse`.
- Extra config: `./clickhouse/disable-telemetry.xml`.
- Uses tuned `ulimits.nofile` for production-like workloads.

## Operations
- Restart stack: `./restart-docker.sh`.
- Update images and restart: `./update-docker.sh`.

## AI Working Notes
- Keep telemetry disable config mounted read-only.
- Credentials come from `.env` (`CLICKHOUSE_DB`, `CLICKHOUSE_USER`, `CLICKHOUSE_PWD`).
- Avoid lowering file descriptor limits without performance testing.
