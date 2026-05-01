# Plan de blindaje del homelab

> Plan de seguridad para mejorar la red del homelab paso a paso, evitando romper servicios críticos como DNS local, Tailscale, Proxmox o Nginx Proxy Manager.

## Objetivo

Reducir exposición, ordenar accesos y preparar la red para una segmentación más segura.

## Principios

- No tocar reglas críticas sin backup previo.
- No abrir puertos permanentes en el router principal.
- Mantener acceso remoto privado mediante Tailscale.
- No exponer paneles sensibles directamente a Internet.
- Separar servicios por nivel de confianza.
- Documentar cada cambio importante.

## Fase 1: Auditoría sin cambios

Objetivo: comprobar el estado actual sin modificar nada.

Tareas:

- Revisar puertos abiertos en el router principal.
- Revisar servicios activos en Proxmox.
- Revisar servicios activos en Raspberry Pi.
- Revisar dominios internos `.lab`.
- Revisar accesos por Tailscale.
- Revisar reglas actuales de OPNsense.
- Revisar qué servicios tienen proxy en Nginx Proxy Manager.

Resultado esperado:

- Saber qué está expuesto.
- Saber qué depende de DNS local.
- Saber qué servicios son críticos.
- Saber qué se puede aislar más adelante.

## Fase 2: Backups antes de tocar

Objetivo: tener forma de volver atrás.

Backups mínimos:

- Configuración de Proxmox.
- Snapshots de CTs y VMs importantes.
- Configuración de OPNsense.
- Configuración de Nginx Proxy Manager.
- Configuración de Pi-hole.
- Configuración de Tailscale documentada.
- Copia de documentación privada.

## Fase 3: Reglas base de seguridad

Objetivo: definir reglas antes de aplicarlas.

Reglas objetivo:

| Zona | Regla |
|---|---|
| Invitados | Solo Internet |
| IoT | Internet limitado, sin acceso a LAN ni Lab |
| LAN principal | Puede administrar servicios internos necesarios |
| Lab / Servidores | No inicia conexiones hacia LAN salvo excepción |
| DMZ | No accede a LAN ni Lab salvo excepción concreta |
| Tailscale | Acceso privado controlado |
| Internet | Sin acceso directo al homelab salvo túneles controlados |

## Fase 4: Servicios sensibles

Estos servicios deben quedarse en LAN o VPN:

- Proxmox VE
- OPNsense
- SSH
- Vaultwarden
- Nginx Proxy Manager
- Pi-hole admin
- Bases de datos
- Paneles de administración

## Fase 5: Exposición pública controlada

Servicios aceptables para publicar con cuidado:

- Portfolio
- Documentación pública
- Página de estado
- Demos temporales
- Webs estáticas

Condiciones:

- Servicio aislado.
- Sin credenciales reutilizadas.
- HTTPS.
- Logs revisados.
- Sin panel admin abierto.
- Sin acceso directo a LAN.
- Preferiblemente detrás de Cloudflare Access si no es público.

## Fase 6: Implementación por etapas

Orden recomendado:

1. Auditar sin cambiar nada.
2. Hacer backups.
3. Confirmar que Tailscale funciona.
4. Probar reglas en entorno Lab.
5. Separar invitados.
6. Separar IoT.
7. Separar servidores.
8. Evaluar DMZ.
9. Revisar exposición de `caarrasco.dev`.
10. Documentar resultados.

## Checklist antes de tocar firewall

- [ ] Tengo acceso físico o local si algo falla.
- [ ] Tengo backup de configuración.
- [ ] Tengo snapshot de servicios importantes.
- [ ] Sé qué regla voy a cambiar.
- [ ] Sé cómo revertirla.
- [ ] Tailscale funciona.
- [ ] DNS local funciona.
- [ ] No estoy tocando varias cosas a la vez.

## Checklist antes de publicar un servicio

- [ ] El servicio no es Proxmox, OPNsense, SSH, Vaultwarden ni NPM.
- [ ] Está aislado del resto de la red.
- [ ] No contiene secretos.
- [ ] Tiene HTTPS.
- [ ] No usa credenciales por defecto.
- [ ] Está actualizado.
- [ ] Tiene logs revisables.
- [ ] Se puede apagar rápido.
- [ ] Está documentado.
