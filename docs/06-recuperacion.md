# 06. Plan de Recuperación ante Desastres (DRP)

## 6.1 Escenarios de Fallo

| Escenario | Impacto | Tiempo de Recuperación (RTO) | Punto de Recuperación (RPO) |
|-----------|---------|------------------------------|------------------------------|
| Caída de Apache | Web no accesible | 15 minutos | 0 (sin pérdida de datos) |
| Corrupción de BBDD | Datos inaccesibles | 1 hora | 24 horas (último backup) |
| Fallo de disco | Pérdida total | 4 horas | 24 horas |
| Ataque de seguridad | Servicio comprometido | 2 horas | Variable |

## 6.2 Procedimiento de Restauración de BBDD

### Paso 1: Detener el servicio
```bash
sudo systemctl stop mysql
```

### Paso 2: Localizar el último backup válido
```bash
ls -lh /backups/mysql/
sha256sum -c /backups/mysql/checksums_$(date +%F).txt
```

### Paso 3: Restaurar la base de datos
```bash
gunzip /backups/mysql/web_db_$(date +%F).sql.gz
mysql -u root -p web_db < /backups/mysql/web_db_$(date +%F).sql
```

### Paso 4: Reiniciar y verificar
```bash
sudo systemctl start mysql
mysql -u root -p -e "SHOW DATABASES; USE web_db; SHOW TABLES;"
```

## 6.3 Procedimiento de Restauración Web

```bash
# Detener Apache
sudo systemctl stop apache2

# Restaurar desde el último backup
rsync -avz /backups/www/html_$(date +%F)/ /var/www/html/

# Ajustar permisos
chown -R www-data:www-data /var/www/html/
chmod -R 755 /var/www/html/

# Reiniciar Apache
sudo systemctl start apache2
```

## 6.4 Pruebas de Recuperación

- **Frecuencia**: Mensual (primer sábado de cada mes)
- **Entorno**: Máquina virtual de pruebas con snapshot previo
- **Documentación**: Registrar resultados en `docs/06-recuperacion.md` (sección inferior)
- **Responsable**: Rotativo entre los miembros del equipo

### Registro de Pruebas

| Fecha | Escenario probado | Resultado | Tiempo real | Observaciones |
|-------|-------------------|-----------|-------------|---------------|
| | | | | |
