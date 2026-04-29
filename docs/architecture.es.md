# Arquitectura del homelab

## Resumen

El homelab está compuesto por un host principal con Proxmox VE, una Raspberry Pi 4 como nodo auxiliar y una red de laboratorio gestionada mediante OPNsense.

La arquitectura actual prioriza tres ideas:

1. Aprender redes y servicios reales sin gastar demasiado.
2. Mantener los servicios internos accesibles de forma cómoda mediante dominios `.lab`.
3. Evitar exposición innecesaria a Internet.

## Capas principales

### Red doméstica principal

La red principal usa el rango `192.168.0.0/24`. Aquí viven los equipos domésticos, el host Proxmox, la Raspberry Pi y varios servicios internos.

### Host Proxmox VE

El servidor Proxmox VE actúa como núcleo del laboratorio. En él se ejecutan contenedores LXC y máquinas virtuales para servicios concretos.

Funciones del host:

- Virtualización.
- Gestión de CTs y VMs.
- Snapshots y backups.
- Almacenamiento local.
- Laboratorio de servicios self-hosted.

### Raspberry Pi 4

La Raspberry Pi 4 actúa como nodo auxiliar. Aloja servicios de red que conviene mantener separados del host principal.

Servicios asociados:

- Pi-hole secundario.
- Nginx Proxy Manager.
- Tailscale.

### Red de laboratorio con OPNsense

OPNsense se usa como firewall/router de laboratorio. Su objetivo es practicar segmentación, NAT, reglas de firewall, DHCP por red y separación entre zonas.

Actualmente existe una red de laboratorio `192.168.50.0/24`, con una VM Debian Lab como cliente de pruebas.

## Diagrama

![Topología pública](../topology-public.png)

