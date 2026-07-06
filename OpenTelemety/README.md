# OpenTelemetry Collector

Collector `otel/opentelemetry-collector-contrib` para el proxy nginx.

## Uso

```bash
docker compose -f otel-col.yml up -d
```

## Variables

No requiere contraseñas ni secretos en este archivo.

## Requisitos externos (rutas del host)

| Ruta en el host | Uso |
|---|---|
| `/compartido/otel-col/config-nginx.yaml` | Configuración del collector (pipelines, exporters, etc.). Si algún exporter allí definido usa credenciales (p. ej. endpoint con API key), gestiónalas dentro de ese archivo, fuera del repo. |

## Redes externas requeridas

- `victoriametrics_vm_net2`
- `wordpress_rossy_default`
