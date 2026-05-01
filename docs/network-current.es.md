# Mapa actual de red

> Documento público y sanitizado de la red actual del homelab.  
> No se publican IPs exactas de máquinas concretas, credenciales, hostnames privados reales ni endpoints sensibles.

## Resumen

La red actual está formada por una red doméstica principal, un entorno de laboratorio con OPNsense, servicios internos en Proxmox, una Raspberry Pi auxiliar y acceso remoto privado mediante Tailscale.

## Topología resumida

```text
Internet
   |
Router principal del operador
   |
Red doméstica principal
   |
   +-- Proxmox VE
   |     |
   |     +-- LXC: Pi-hole
   |     +-- LXC: Uptime Kuma
   |     +-- LXC: Debian Files/Web
   |     +-- LXC: Vaultwarden
   |     +-- LXC: ProxBot
   |     +-- VM: OPNsense
   |     +-- VM: Debian Lab
   |
   +-- Raspberry Pi
   |     |
   |     +-- Pi-hole secundario
   |     +-- Nginx Proxy Manager
   |     +-- Tailscale
   |
   +-- Dispositivos personales
   |
   +-- Dispositivos IoT / domésticos
```

## Redes actuales

| Zona | Rango documentado | Uso | Estado |
|---|---:|---|---|
| Red principal | `192.168.0.0/24` | Dispositivos domésticos, Proxmox, Raspberry Pi y servicios principales | Activa |
| Red de laboratorio | `192.168.50.0/24` | Pruebas con OPNsense y máquinas de laboratorio | Activa/en pruebas |
| Tailscale | `100.x.x.x` | Acceso remoto privado | Activa |

## Servicios principales

| Servicio | Ubicación | Uso | Exposición |
|---|---|---|---|
| Proxmox VE | Host físico | Virtualización principal | Local only |
| Pi-hole | LXC / Raspberry Pi | DNS local y filtrado | Local only |
| Uptime Kuma | LXC | Monitorización | Local only |
| Nginx Proxy Manager | Raspberry Pi | Reverse proxy interno | Local only |
| Vaultwarden | LXC | Gestor de contraseñas en laboratorio | Local only |
| OPNsense | VM | Firewall/laboratorio de red | Lab network |
| Debian Lab | VM | Cliente de pruebas dentro del lab | Lab network |
| ProxBot | LXC | Bot de Discord para gestión/aprendizaje | Development |
| Tailscale | Raspberry Pi / clientes | Acceso remoto privado | Private access |
| Cloudflare Tunnel | Servicio temporal | Exposición puntual controlada | Temporary tunnel |

## Dominios internos

El homelab usa dominios internos `.lab` resueltos mediante DNS local y reverse proxy interno.

Ejemplos públicos sanitizados:

| Dominio interno | Uso |
|---|---|
| `proxmox.lab` | Acceso interno al panel de Proxmox |
| `pihole.lab` | Acceso interno a Pi-hole |
| `kuma.lab` | Acceso interno a Uptime Kuma |
| `npm.lab` | Acceso interno a Nginx Proxy Manager |
| `vault.lab` | Acceso interno a Vaultwarden |

## Acceso remoto

El acceso remoto se realiza mediante Tailscale. No se documentan públicamente IPs exactas de Tailnet ni rutas privadas.

```text
Cliente autorizado
   |
Tailscale
   |
Raspberry Pi / nodo autorizado
   |
Servicios internos permitidos
```

## Exposición externa

La exposición externa se mantiene limitada y controlada. No hay puertos permanentes abiertos en el router principal.

```text
Usuario externo
   |
Cloudflare
   |
Cloudflare Tunnel temporal
   |
Servicio concreto aislado
```

## Riesgos a revisar

- Separar mejor la red doméstica, servidores, IoT e invitados.
- Revisar que no existan puertos abiertos innecesarios.
- Limitar acceso a paneles sensibles.
- Mantener Proxmox, OPNsense, Vaultwarden y NPM solo en red local o acceso privado.
- Documentar reglas de firewall antes de aplicarlas.
- Crear backups de configuración antes de tocar red o firewall.

## Próximos pasos

- Crear mapa objetivo de red.
- Definir segmentación LAN / Lab / IoT / Guest / DMZ.
- Definir reglas base de firewall.
- Crear política para exposición de servicios bajo dominio propio.
- Crear checklist de seguridad antes de publicar cualquier servicio.
