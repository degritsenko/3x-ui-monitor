# 3x-ui Monitoring

This stack runs Prometheus, Grafana, node-exporter, and `zbndev/3x-ui-exporter` separately from the existing 3x-ui Docker Compose stack.

## Setup

Copy the example environment file:

```bash
cp .env.example .env
```

Edit `.env`:

- `XUI_BASE_URL`: full URL of the 3x-ui panel.
- `XUI_API_TOKEN`: API token from `Settings -> Security -> API Token`.
- `GRAFANA_ADMIN_USER`: Grafana admin username.
- `GRAFANA_ADMIN_PASSWORD`: Grafana admin password.

## Start

```bash
docker compose up -d
```

## URLs

- Grafana: `http://<server-ip>:3000`
- Prometheus: `http://127.0.0.1:9090`
- 3x-ui exporter metrics: `http://127.0.0.1:9847/metrics`
- node-exporter metrics: `http://127.0.0.1:9100/metrics`

## Verify

```bash
docker compose ps
docker compose logs xui-exporter
```

In Prometheus, open `Status -> Targets` and confirm that `3x-ui` and `node` are up.

In Grafana, open the `3x-ui` folder and select the provisioned dashboard.
