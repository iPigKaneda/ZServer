# Stack: OpenEMR

Stack de Docker Compose para desplegar OpenEMR 8.0.0 + MariaDB 11.4.
Pensado para publicarse en el repo `zserver` y ser referenciado por Portainer
como stack de tipo "Repository".

## Contenido
- `docker-compose.yml` — definición del stack (usa variables de entorno, sin secretos hardcodeados).
- `.env.example` — plantilla de las variables requeridas. Copiar a `.env` y rellenar antes de desplegar.

## Uso con Git (antes de subir)
```bash
cd zserver
git add stacks/openemr
git commit -m "Add OpenEMR stack"
git push
```

Agrega `.env` a tu `.gitignore` global del repo para no subir contraseñas reales:
```
stacks/openemr/.env
```

## Configurar en Portainer

1. Ve a **Stacks → Add stack**.
2. En **Build method**, elige **Repository**.
3. Repository URL: la URL de tu repo `zserver` (https o git+ssh según cómo lo tengas configurado en Portainer).
4. Repository reference: la rama (ej. `main`).
5. Compose path: `stacks/openemr/docker-compose.yml`.
6. En **Environment variables**, agrega manualmente (o sube el `.env`) los valores de:
   - `MYSQL_ROOT_PASSWORD`
   - `OE_USER`
   - `OE_PASS`
   - `OPENEMR_HOST_PORT` (opcional, default 8443)
7. Activa **GitOps updates** si quieres que Portainer haga redeploy automático cuando hagas push a la rama.
8. Deploy the stack.

## Primer acceso

Una vez arriba (puede tardar 2-5 min la primera vez mientras corre la instalación automática):

```
https://TU_IP_O_DOMINIO:<OPENEMR_HOST_PORT>
```

Login con `OE_USER` / `OE_PASS` definidos en el `.env`. El certificado es
autofirmado por defecto — acepta la excepción del navegador la primera vez.

**Importante**: cambia la contraseña de admin desde la propia UI de OpenEMR
después del primer login; no dejes la del `.env` como definitiva.

## Volúmenes persistentes

- `openemr_mysql_data` — base de datos.
- `openemr_sites` — configuración, documentos, y **datos de pacientes**. Es el volumen crítico: haz backup regular de este volumen.
- `openemr_ssl` — certificados.