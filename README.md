# ZServer
Proyecto de Servicios con Portrainer

## Configuración de credenciales

Ningún archivo `.yml` de este repo contiene contraseñas ni claves en texto plano: todas se leen
de variables de entorno (`${VARIABLE}`). Cada carpeta de stack incluye:

- `.env.example` — lista de variables que necesitas definir (sí se versiona, no tiene valores reales).
- `.env` — el que tú creas localmente con los valores reales (**no se versiona**, ver `.gitignore`).
- `README.md` — qué variables requiere ese stack y cuáles son contraseñas/secretos.

Para levantar un stack:

```bash
cd <Carpeta-del-stack>
cp .env.example .env   # y rellena los valores reales
docker compose -f <archivo>.yml up -d
```

## Stacks incluidos

| Carpeta | Servicio | ¿Requiere contraseña? |
|---|---|---|
| [Dynatrace/](Dynatrace/) | Demo easyTravel + Datadog agent | Sí |
| [Minecraft/](Minecraft/) | Servidor Bedrock | No |
| [Nginx/](Nginx/) | Proxy nginx + OTel | No |
| [OpenTelemety/](OpenTelemety/) | OTel Collector | No |
| [Openobserve/](Openobserve/) | Openobserve | Sí |
| [PaginaRossy/](PaginaRossy/) | WordPress (2 sitios) + MySQL | Sí |
| [SSH/](SSH/) | Cliente SSH | No |
| [Victoriametrics/](Victoriametrics/) | VictoriaMetrics + vmagent + Grafana | Sí |
| [VisualCode/](VisualCode/) | code-server | Sí |
| [Zabbix/](Zabbix/) | Zabbix server + web + PostgreSQL | Sí |

Nota: existen copias duplicadas de estos stacks en `Stack/` y `Stack copy/`, mantenidas en
sincronía con los mismos cambios.
