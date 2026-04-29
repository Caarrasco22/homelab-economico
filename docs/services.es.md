# Servicios del homelab

## Tabla de servicios

| ID | Servicio | Tipo | Función |
|---|---|---|---|
| Host | Proxmox VE | Host físico | Virtualización y gestión del laboratorio |
| CT 100 | Pi-hole | LXC | DNS local y bloqueo de publicidad |
| CT 101 | Uptime Kuma | LXC | Monitorización de servicios |
| CT 102 | Debian Files/Web | LXC | Samba, Nginx, Python 3 HTTP server y Cloudflare Tunnel temporal |
| CT 103 | Vaultwarden | LXC | Gestor de contraseñas self-hosted |
| VM 104 | OPNsense | VM | Firewall y red de laboratorio |
| VM 105 | Debian Lab | VM | Cliente de pruebas dentro de la Lab LAN |
| CT 106 | ProxBot v1 | LXC | Bot de Discord en desarrollo |
| Nodo auxiliar | Raspberry Pi 4 | Hardware externo | Pi-hole secundario, NPM y Tailscale |

## Pi-hole

Pi-hole se utiliza para DNS local y bloqueo de publicidad. También permite resolver dominios internos `.lab` para acceder cómodamente a los servicios internos.

## Nginx Proxy Manager

Nginx Proxy Manager se usa para gestionar accesos web internos mediante dominios `.lab`. Permite que servicios con puertos diferentes sean accesibles con nombres más cómodos.

Ejemplos documentados:

- `pihole.lab`
- `kuma.lab`
- `vault.lab`
- `npm.lab`
- `proxmox.lab`

## Uptime Kuma

Uptime Kuma monitoriza servicios internos y ayuda a comprobar de forma visual si están levantados.

## Vaultwarden

Vaultwarden se utiliza como gestor de contraseñas self-hosted ligero. En una publicación pública no se deben mostrar usuarios, dominios reales, tokens ni capturas de bóvedas.

## CT 102: Debian Files/Web

Este contenedor concentra servicios prácticos para compartir archivos y levantar pruebas rápidas:

- Samba para red local.
- Nginx para web/proxy interno.
- Python 3 para servidor HTTP temporal.
- Cloudflare Tunnel para compartir enlaces temporales sin abrir puertos permanentes.

## OPNsense

OPNsense se ejecuta como VM para crear una red de laboratorio separada. Actualmente sirve para practicar:

- WAN/LAN.
- NAT.
- Reglas de firewall.
- Segmentación.
- DHCP por red.
- Futuras VLANs/subredes.

## ProxBot v1

ProxBot v1 es un bot de Discord en desarrollo. Su propósito es aprender automatización y crear una herramienta útil para consultar o gestionar partes del homelab.

Objetivos técnicos:

- Usar configuración externa en `config.json`.
- Evitar valores hardcodeados.
- Consultar estado de servicios.
- Ejecutar comandos controlados.
- Documentar el aprendizaje del desarrollo del bot.
