# Zabbix (server + web) con PostgreSQL

Dos compose independientes que comparten la misma base PostgreSQL externa:

- `zabbix.yml` → `zabbix-server-pgsql`
- `zabbix-nginx.yml` → `web-nginx-pgsql` (frontend)

## Uso

```bash
cp .env.example .env   # y rellena los valores
docker compose -f zabbix.yml up -d
docker compose -f zabbix-nginx.yml up -d
```

## Variables requeridas (.env)

| Variable | Requiere contraseña/secreto | Descripción |
|---|---|---|
| `POSTGRES_USER` | No (pero determina el acceso) | Usuario de PostgreSQL. Debe ser el mismo en ambos archivos. |
| `POSTGRES_PASSWORD` | Sí | Password de PostgreSQL. Debe ser el mismo en ambos archivos. |

## Requisitos externos

- `DB_SERVER_HOST: postgresql` — ninguno de estos dos archivos define el servicio `postgresql`;
  debe existir como contenedor/servicio externo en la misma red `victoriametrics_vm_net2`, con el
  usuario/password anteriores ya creados en esa base.
- `zabbix.yml` monta `/externalHD/postgresql:/var`, una ruta local del host.

## Redes externas requeridas

- `victoriametrics_vm_net2`
