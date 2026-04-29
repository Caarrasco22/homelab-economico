# Seguridad y privacidad

## Datos que no se publican

Este repositorio no debe incluir:

- Contraseñas.
- Usuarios reales.
- Correos personales.
- IPs exactas de equipos concretos.
- IP exacta de Tailscale.
- Tokens de Discord, Cloudflare o APIs.
- Capturas con sesiones abiertas.
- Rutas internas con datos personales.
- Nombres reales de equipos si identifican a una persona.

## Decisiones de seguridad actuales

- No hay puertos permanentes abiertos en el router principal.
- El acceso remoto se realiza con Tailscale.
- Cloudflare Tunnel se usa solo para exposición temporal cuando hace falta.
- Los dominios `.lab` son internos.
- Se separa la red principal de la red de laboratorio mediante OPNsense.
- El proyecto se documenta con IPs anonimizadas o rangos generales.

## Recomendaciones antes de subir capturas

Antes de publicar imágenes o capturas en GitHub:

1. Revisar la barra del navegador.
2. Ocultar IPs concretas si no son necesarias.
3. Ocultar nombres de usuario.
4. Cerrar sesiones sensibles.
5. Revisar que no aparezcan tokens, rutas personales ni correos.
6. Evitar capturas de paneles con claves API o configuración completa de túneles.

## Buenas prácticas futuras

- Usar `.env` para secretos.
- Mantener `config.example.json` público y `config.json` privado.
- Añadir `.gitignore` desde el inicio.
- Documentar comandos sin incluir credenciales.
- Mantener backups de configuraciones importantes.
- Revisar permisos de Samba.
- Separar IoT e invitados cuando OPNsense pase a producción.
