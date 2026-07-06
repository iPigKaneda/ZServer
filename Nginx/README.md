# Nginx (proxy con módulo OpenTelemetry)

Proxy nginx (imagen `nginx-otel:latest`, construida aparte) que expone 80/443/3000 y sirve como
entrada compartida para otros stacks (Victoriametrics, WordPress/Rossy).

## Uso

```bash
docker compose -f ngnix-otel.yml up -d
```

## Variables

No requiere contraseñas ni secretos en este archivo.

## Requisitos externos (rutas del host)

| Ruta en el host | Uso |
|---|---|
| `/compartido/nginx/conf.d/default.conf` | Config principal de nginx (ver `compartido/nginx/conf.d/`). |
| `/compartido/nginx/includes/proxy.conf` | Includes de proxy (ver `compartido/nginx/includes/`). |
| `/compartido/nginx/certificados/...` | Certificados TLS (privados) — no incluidos en el repo, deben existir en el host. |

## Redes externas requeridas

- `victoriametrics_vm_net2`
- `wordpress_rossy_default`

Ambas deben existir previamente (`docker network create ...` o creadas por los stacks
Victoriametrics/PaginaRossy).
