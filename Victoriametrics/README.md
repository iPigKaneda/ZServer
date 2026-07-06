# VictoriaMetrics + vmagent + Grafana

Stack de métricas: VictoriaMetrics (almacenamiento), vmagent (scraping) y Grafana (visualización,
detrás de TLS con `VIRTUAL_HOST`/`LETSENCRYPT_HOST`, pensado para un proxy tipo nginx-proxy).

## Uso

```bash
cp .env.example .env   # y rellena los valores
docker compose -f victoriametrics.yml up -d
```

## Variables requeridas (.env)

| Variable | Requiere contraseña/secreto | Descripción |
|---|---|---|
| `GF_SECURITY_ADMIN_USER` | No (pero es la cuenta admin) | Usuario administrador de Grafana. |
| `GF_SECURITY_ADMIN_PASSWORD` | Sí | Password del administrador de Grafana. **Antes de este cambio no estaba definida y Grafana quedaba con el default `admin`/`admin`.** |

## Requisitos externos (rutas del host)

| Ruta en el host | Uso |
|---|---|
| `/compartido/vmetrics/prometheus-vm-single.yml` | Config de scraping de vmagent. |
| `/certificados/grafana_private.key`, `/certificados/grafana_certificate.crt` | Certificado TLS de Grafana (privados, no incluidos en el repo). |

## Notas

- `--vmalert.proxyURL=http://192.168.3.34:8880` apunta a una IP fija de la red interna; no es una
  credencial, pero revisa que siga siendo correcta si cambia la topología de red.
