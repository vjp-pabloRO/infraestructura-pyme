# 02. Diseño de la Infraestructura

## 2.1 Arquitectura Lógica
```text
[Internet]
   │
   ▼
[Firewall / UFW] → Puertos: 22(SSH), 80(HTTP), 443(HTTPS)
   │
   ▼
[Servidor Ubuntu 22.04 LTS]
   ├── Apache 2.4 + PHP 8.1  (Web Pública + Gestión Interna)
   ├── MariaDB 10.6          (web_db + gestion_db)
   ├── Netdata               (Monitorización local en puerto 19999)
   └── Cron Jobs             (mysqldump + rsync para backups)
``` 
## 2.2 Tabla de Software y Versiones

| Componente       | Versión      | Función                             |
|------------------|--------------|-------------------------------------|
| Ubuntu Server    | 22.04 LTS    | Sistema Operativo base              |
| Apache           | 2.4.59       | Servidor Web y proxy inverso básico |
| PHP              | 8.1          | Motor de ejecución para la web      |
| MariaDB          | 10.6         | Gestor de Base de Datos             |
| Netdata          | 1.38+        | Monitorización en tiempo real       |
| UFW              | 0.36         | Firewall de aplicación              |
| Certbot          | 2.x          | Certificados SSL/TLS automáticos    |
| HAProxy          | 2.6          | Balanceador de carga y proxy inverso|

## 2.3 Esquema de Red y Puertos

- **IP Servidor**: `192.168.1.100` (LAN) / IP pública asignada por ISP
- **SSH**: `22/tcp` → solo desde IP de oficina/administración
- **Web**: `80/tcp` → redirige automáticamente a `443/tcp` (HTTPS obligatorio)
- **Base de Datos**: `3306/tcp` → **bloqueado externamente**, solo acceso local `127.0.0.1`
- **Monitorización**: `19999/tcp` → acceso restringido por túnel SSH o VPN

## 2.4 Consideraciones de Seguridad

- Deshabilitar login `root` por SSH (`PermitRootLogin no` en `/etc/ssh/sshd_config`)
- Autenticación SSH solo por claves (`PasswordAuthentication no`)
- Actualizaciones automáticas: paquete `unattended-upgrades`
- Principio de mínimo privilegio: usuarios de BBDD separados por aplicación
