# Checklist de auditoría de seguridad

> Checklist para revisar el estado actual del homelab sin hacer cambios destructivos.

## Router principal

- [ ] Revisar si hay puertos abiertos.
- [ ] Revisar si hay reglas de port forwarding.
- [ ] Revisar UPnP.
- [ ] Revisar dispositivos conectados.
- [ ] Revisar reservas DHCP.

## Proxmox

- [ ] Revisar usuarios.
- [ ] Revisar 2FA.
- [ ] Revisar VMs y CTs activos.
- [ ] Revisar snapshots.
- [ ] Revisar backups.
- [ ] Revisar acceso SSH.
- [ ] Revisar actualizaciones pendientes.

## Raspberry Pi

- [ ] Revisar servicios activos.
- [ ] Revisar acceso SSH.
- [ ] Revisar Tailscale.
- [ ] Revisar Pi-hole.
- [ ] Revisar Nginx Proxy Manager.
- [ ] Revisar actualizaciones pendientes.

## Pi-hole

- [ ] Revisar registros DNS locales.
- [ ] Revisar dominios `.lab`.
- [ ] Revisar clientes DNS.
- [ ] Revisar contraseña admin.
- [ ] Revisar si la interfaz admin está solo en LAN.

## Nginx Proxy Manager

- [ ] Revisar proxy hosts creados.
- [ ] Revisar credenciales.
- [ ] Revisar certificados.
- [ ] Revisar qué servicios pasan por proxy.
- [ ] Confirmar que no hay paneles sensibles publicados.

## OPNsense

- [ ] Revisar interfaces.
- [ ] Revisar reglas LAN/WAN.
- [ ] Revisar NAT.
- [ ] Revisar aliases.
- [ ] Revisar logs.
- [ ] Revisar si sigue siendo laboratorio o pasará a firewall central.

## Tailscale

- [ ] Revisar dispositivos autorizados.
- [ ] Revisar claves antiguas.
- [ ] Revisar si hay exit node.
- [ ] Revisar si hay subnet routes.
- [ ] Revisar permisos de dispositivos.

## Cloudflare / caarrasco.dev

- [ ] Revisar DNS público.
- [ ] Revisar túneles activos.
- [ ] Revisar si hay servicios expuestos.
- [ ] Revisar Cloudflare Access.
- [ ] Confirmar que no hay paneles internos públicos.

## GitHub

- [ ] Revisar que no hay IPs exactas privadas innecesarias.
- [ ] Revisar que no hay tokens.
- [ ] Revisar que no hay contraseñas.
- [ ] Revisar que no hay capturas con datos sensibles.
- [ ] Revisar Dependabot y secret scanning.
