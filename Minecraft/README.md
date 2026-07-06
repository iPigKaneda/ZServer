# Minecraft Bedrock Server

Servidor Minecraft Bedrock (`itzg/minecraft-bedrock-server`).

## Uso

```bash
docker compose -f minecraft.yml up -d
```

## Variables

No requiere contraseñas ni secretos. Variables de configuración del propio archivo (no sensibles):

| Variable | Requiere contraseña/secreto | Descripción |
|---|---|---|
| `EULA` | No | Aceptación del EULA de Mojang, debe ser `"TRUE"`. |
| `OPS` | No* | Lista de XUID de las cuentas con permisos de operador. No es una credencial (no autentica nada por sí sola), pero identifica cuentas reales — evita publicarla si prefieres no exponer qué jugadores son admins. |
| `GAMEMODE`, `DIFFICULTY`, `LEVEL_NAME`, `MAX_PLAYERS` | No | Configuración del mundo/servidor. |

## Notas

- El volumen `/minecraft/bedrock/sanpedro:/data` es una ruta local del host; ajústala a tu entorno.
