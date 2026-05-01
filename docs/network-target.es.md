# Mapa objetivo de red

> Diseño futuro de segmentación y seguridad del homelab.

## Objetivo

Separar la red en zonas con diferentes niveles de confianza para reducir riesgos y controlar mejor qué puede hablar con qué.

## Zonas propuestas

| Zona | Rango documentado | Uso |
|---|---:|---|
| LAN principal | `192.168.0.0/24` | PCs, móviles personales, impresoras y dispositivos de confianza |
| Lab / Servidores | `192.168.50.0/24` | Proxmox, VMs, LXCs y servicios internos |
| IoT | `192.168.60.0/24` | Smart TV, domótica, dispositivos poco confiables |
| Invitados | `192.168.70.0/24` | Wi-Fi invitados, solo Internet |
| DMZ opcional | `192.168.80.0/24` | Servicios públicos aislados |
| Tailscale | `100.x.x.x` | Acceso remoto privado |

## Principio base

```text
Lo que no necesita comunicarse, no se comunica.
```

## Reglas objetivo

| Origen | Destino | Política |
|---|---|---|
| LAN principal | Lab / Servidores | Permitido solo administración necesaria |
| LAN principal | IoT | Permitido solo si hace falta |
| IoT | LAN principal | Bloqueado |
| IoT | Lab / Servidores | Bloqueado |
| Invitados | LAN principal | Bloqueado |
| Invitados | Lab / Servidores | Bloqueado |
| Invitados | Internet | Permitido |
| DMZ | LAN principal | Bloqueado |
| DMZ | Lab / Servidores | Bloqueado salvo excepciones |
| Tailscale | Servicios internos | Permitido según usuario/dispositivo |
| Internet | Homelab | Bloqueado salvo túneles controlados |

## Servicios sensibles

Estos servicios no deben exponerse directamente a Internet:

- Proxmox VE
- OPNsense
- SSH
- Vaultwarden
- Nginx Proxy Manager
- Bases de datos
- Paneles de administración
- Servicios en desarrollo

## Servicios publicables con control

Estos servicios podrían publicarse si están aislados y protegidos:

- Web estática
- Portfolio
- Documentación pública
- Página de estado pública
- Demo controlada de proyecto

## Acceso remoto recomendado

- Tailscale para administración privada.
- Cloudflare Access para servicios privados con dominio.
- Cloudflare Tunnel solo para servicios concretos.
- Sin port forwarding permanente en el router principal.

## Próximas decisiones

- Decidir si OPNsense será firewall central real o seguirá como laboratorio.
- Decidir dónde vivirá la DMZ.
- Decidir qué servicios podrán tener dominio público.
- Crear reglas de firewall paso a paso.
- Hacer backup antes de cada cambio grande.
