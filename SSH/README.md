# SSH client

Contenedor Ubuntu con acceso a red del host (`network_mode: host`) pensado como cliente SSH
persistente.

## Uso

```bash
docker compose -f ssh.yml up -d
```

## Variables

No requiere contraseñas ni secretos en este archivo — no hay credenciales hardcodeadas.

## Requisitos externos

- Monta `~/.ssh` del host en modo solo lectura (`~/.ssh:/root/.ssh:ro`). Las claves/llaves privadas
  deben existir ya en el host; este stack no las genera ni las contiene.
- `network_mode: host` + `cap_add: NET_ADMIN`: el contenedor comparte la red del host, ten en
  cuenta el alcance de permisos al desplegarlo en un servidor compartido.
