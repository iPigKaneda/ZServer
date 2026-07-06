# Openobserve

Stack de Openobserve (observabilidad: logs/métricas/trazas).

## Uso

```bash
cp .env.example .env   # y rellena los valores
docker compose -f openobserve.yml up -d
```

## Variables requeridas (.env)

| Variable | Requiere contraseña/secreto | Descripción |
|---|---|---|
| `ZO_ROOT_USER_EMAIL` | No (pero es la cuenta root) | Email del usuario root inicial. |
| `ZO_ROOT_USER_PASSWORD` | Sí | Password del usuario root inicial. Úsalo solo para el primer login y crea usuarios adicionales después. |

## Redes externas requeridas

- `victoriametrics_vm_net2`
- `wordpress_rossy_default`
