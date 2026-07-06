# VisualCode — code-server

code-server (VS Code en el navegador), imagen `linuxserver/code-server`.

## Uso

```bash
cp .env.example .env   # y rellena los valores
docker compose -f vscode.yml up -d
```

## Variables requeridas (.env)

| Variable | Requiere contraseña/secreto | Descripción |
|---|---|---|
| `CODE_SERVER_PASSWORD` | Sí | Password para acceder a la interfaz web de code-server. |
| `CODE_SERVER_SUDO_PASSWORD` | Sí | Password para usar `sudo` dentro del contenedor. |

## Notas

- Existe una alternativa más segura, comentada en el yml: usar `HASHED_PASSWORD` /
  `SUDO_PASSWORD_HASH` (hash en vez de texto plano) en lugar de `PASSWORD`/`SUDO_PASSWORD`. Si la
  activas, define `CODE_SERVER_HASHED_PASSWORD` / `CODE_SERVER_SUDO_PASSWORD_HASH` en tu `.env`.
