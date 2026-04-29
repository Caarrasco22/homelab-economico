# Checklist de fotos y capturas para documentar el homelab

## Fotos físicas recomendadas

Haz fotos horizontales, con buena luz y sin papeles/datos personales de fondo.

### 1. Vista general del setup

Foto del espacio donde esté el homelab: router, AP, servidor, Raspberry Pi y cableado general.

Evitar mostrar:

- Dirección de casa.
- Facturas o papeles.
- Pantallas con datos sensibles.

### 2. Servidor Proxmox

Foto del equipo físico que hace de servidor Proxmox.

Sería útil que se vea:

- Torre/miniPC/servidor.
- Ventilación.
- Ubicación aproximada.
- Cables de red/alimentación ordenados.

### 3. Raspberry Pi 4

Foto de la Raspberry Pi 4, preferiblemente mostrando caja, disipación y cableado.

### 4. Router/AP

Foto del router principal y/o punto de acceso, pero sin mostrar pegatinas con claves Wi-Fi, SSID, número de serie o datos del operador.

### 5. Almacenamiento/cableado

Foto de discos, bahías, adaptadores o cableado si forman parte del aprendizaje del proyecto.

## Capturas de pantalla recomendadas

### 1. Dashboard de Proxmox

Captura del panel principal, ocultando:

- IP exacta si aparece.
- Nombre real del host si es personal.
- Nombres sensibles de almacenamiento.

### 2. Lista de CTs y VMs

Captura donde se vean CT 100, CT 101, CT 102, CT 103, VM 104, VM 105 y CT 106.

### 3. Uptime Kuma

Captura del dashboard de monitorización con nombres genéricos o dominios `.lab`.

### 4. Pi-hole

Captura del dashboard general, evitando mostrar clientes concretos o dominios privados visitados.

### 5. Nginx Proxy Manager

Captura de la lista de hosts/proxy, ocultando detalles sensibles si los hay.

### 6. OPNsense

Captura de la interfaz de OPNsense mostrando estado general o interfaces, sin reglas completas sensibles.

### 7. CT 102

Captura de terminal mostrando servicios instalados o comandos seguros, por ejemplo:

```bash
python3 --version
nginx -v
smbd --version
cloudflared --version
```

Evitar mostrar tokens o URLs completas privadas de Cloudflare Tunnel.

### 8. ProxBot v1

Captura segura del bot en Discord o del código, ocultando:

- Token del bot.
- IDs privados si no quieres publicarlos.
- Nombres de servidores/personas.

## Fotos que NO conviene subir

- Pegatinas del router con claves.
- Pantallas con contraseñas, tokens o sesiones abiertas.
- Cloudflare con túneles/token visible.
- Discord Developer Portal con token del bot.
- Vaultwarden con bóvedas o entradas visibles.
- Samba mostrando carpetas personales.
