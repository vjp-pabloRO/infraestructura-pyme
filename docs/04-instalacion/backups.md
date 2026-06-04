# Estrategia de Copias de Seguridad

## Base de Datos (MySQL/MariaDB)

Se utilizará `mysqldump` para realizar volcados lógicos de las bases de datos `web_db` y `gestion_db`.

### Script de Backup Diario

Guardar en `/usr/local/bin/backup-mysql.sh`:

```bash
#!/bin/bash
DATE=$(date +%F)
BACKUP_DIR="/backups/mysql"
mkdir -p $BACKUP_DIR

# Volcado de las bases de datos
mysqldump -u root -p'TU_PASSWORD_SEGURA' web_db > $BACKUP_DIR/web_db_$DATE.sql
mysqldump -u root -p'TU_PASSWORD_SEGURA' gestion_db > $BACKUP_DIR/gestion_db_$DATE.sql

# Compresión y generación de checksum
gzip $BACKUP_DIR/*.sql
sha256sum $BACKUP_DIR/*.sql.gz > $BACKUP_DIR/checksums_$DATE.txt
```

### Automatización con Cron

Programar la ejecución diaria a las 02:00 AM:

```bash
# crontab -e
0 2 * * * /usr/local/bin/backup-mysql.sh
```

---

## Archivos Web

Se utilizará `rsync` para realizar copias incrementales del directorio web.

### Script de Backup Web

Guardar en `/usr/local/bin/backup-www.sh`:

```bash
#!/bin/bash
DATE=$(date +%F)
BACKUP_DIR="/backups/www"
mkdir -p $BACKUP_DIR

# Copia incremental
rsync -avz --delete /var/www/html/ $BACKUP_DIR/html_$DATE/
```

---

## Política de Rotación y Limpieza

Para evitar llenar el disco, se mantendrán:
- **7 copias diarias**
- **4 copias semanales**

Script de limpieza automática para borrados mayores a 7 días:

```bash
find /backups/mysql -name "*.sql.gz" -mtime +7 -delete
find /backups/www -type d -name "html_*" -mtime +7 -exec rm -rf {} +
```

## Verificación

- Comprobar semanalmente que los logs de `mysqldump` no arrojen errores.
- Validar la integridad de los archivos usando los `checksums`.
- **Obligatorio**: Realizar una prueba de restauración mensual en un entorno de pruebas (ver `docs/06-recuperacion.md`).