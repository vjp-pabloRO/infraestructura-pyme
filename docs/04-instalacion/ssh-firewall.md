# Configuración de SSH y Firewall

## Configuración de firewall con UFW

- `ufw default deny incoming`

## Reglas UFW

- Permitir SSH solo desde IP de la oficina: `ufw allow from 192.168.1.0/24 to any port 22`
- Permitir tráfico web: `ufw allow 80/tcp` y `ufw allow 443/tcp`