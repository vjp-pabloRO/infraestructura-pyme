# 05. Plan de Operación y Mantenimiento

## 5.1 Mantenimiento Preventivo

### Actualizaciones de Seguridad
El servidor se actualizará automáticamente mediante `unattended-upgrades`:

```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

Configuración en `/etc/apt/apt.conf.d/20auto-upgrades`:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```

### Revisión de Logs
Se revisarán semanalmente los siguientes logs:

| Log | Ruta | Comando de consulta |
|-----|------|---------------------|
| Apache | `/var/log/apache2/` | `tail -f /var/log/apache2/error.log` |
| MySQL | `/var/log/mysql/` | `tail -f /var/log/mysql/error.log` |
| Sistema | `/var/log/syslog` | `journalctl -xe` |
| Auth | `/var/log/auth.log` | `grep "Failed" /var/log/auth.log` |

### Limpieza de Disco
Script mensual para limpiar paquetes y logs antiguos:

```bash
#!/bin/bash
# /usr/local/bin/limpieza-mensual.sh
apt autoremove -y
apt clean
find /var/log -name "*.gz" -mtime +30 -delete
journalctl --vacuum-time=30d
```

## 5.2 Monitorización Operativa

- **Diaria**: Revisar dashboard de Netdata (puerto 19999)
- **Semanal**: Verificar espacio en disco (`df -h`) y estado de backups
- **Mensual**: Revisar logs de seguridad y actualizaciones pendientes

## 5.3 Procedimiento de Actualización Manual

1. Hacer backup previo de BBDD y web
2. Ejecutar `sudo apt update && sudo apt upgrade`
3. Reiniciar servicios críticos:
   ```bash
   sudo systemctl restart apache2
   sudo systemctl restart mysql
   ```
4. Verificar que los servicios están activos:
   ```bash
   sudo systemctl status apache2 mysql
   ```
