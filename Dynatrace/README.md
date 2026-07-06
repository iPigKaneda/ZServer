# Dynatrace / easyTravel demo stack

Stack de demo (easyTravel) con MongoDB, backend/frontend Java, frontend Angular, nginx y
agente de Datadog para observabilidad.

## Uso

```bash
cp .env.example .env   # y rellena los valores
docker compose -f easytravel02.yml up -d
```

## Variables requeridas (.env)

| Variable | Requiere contraseña/secreto | Descripción |
|---|---|---|
| `ET_DATABASE_PASSWORD` | Sí | Password del usuario `etAdmin` en MongoDB (`ET_DATABASE_USER`). Debe coincidir con el valor real de la base de datos. |
| `DD_API_KEY` | Sí | API Key de Datadog para el `datadog-agent`. Se obtiene en Datadog → Organization Settings → API Keys. |

## Notas

- El bloque `labels` comentado (integración Datadog Agent + MongoDB check, requiere Mongo v6) también referencia `ET_DATABASE_PASSWORD`; si lo activas, asegúrate de tener el `.env` cargado.
- No hay otras credenciales hardcodeadas en este stack.
