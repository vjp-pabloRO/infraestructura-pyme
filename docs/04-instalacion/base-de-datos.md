# Instalación y Configuración de la Base de Datos (MariaDB)

## 3.1 Instalación

```bash
sudo apt install mariadb-server mariadb-client -y
sudo systemctl enable mariadb
sudo systemctl start mariadb
```

## 3.2 Asegurar la instalación

```bash
sudo mysql_secure_installation
```

Respuestas recomendadas:
- Enter current password for root: (pulsar Enter si no hay)
- Set root password? **Y** → introducir contraseña segura
- Remove anonymous users? **Y**
- Disallow root login remotely? **Y**
- Remove test database? **Y**
- Reload privilege tables? **Y**

## 3.3 Creación de Bases de Datos y Usuarios

```bash
sudo mysql -u root -p
```

Dentro del prompt de MySQL:

```sql
-- Base de datos para la web pública
CREATE DATABASE web_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'web_user'@'localhost' IDENTIFIED BY 'PasswordSegura123!';
GRANT SELECT, INSERT, UPDATE, DELETE ON web_db.* TO 'web_user'@'localhost';

-- Base de datos para gestión interna
CREATE DATABASE gestion_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'gestion_user'@'localhost' IDENTIFIED BY 'PasswordSegura456!';
GRANT ALL PRIVILEGES ON gestion_db.* TO 'gestion_user'@'localhost';

FLUSH PRIVILEGES;
EXIT;
```

## 3.4 Verificación

```bash
mysql -u web_user -p web_db -e "SHOW TABLES;"
mysql -u gestion_user -p gestion_db -e "SHOW TABLES;"
```

## 3.5 Copia de Seguridad Inicial

```bash
sudo mysqldump -u root -p --all-databases > /backups/mysql/initial_full_backup.sql
```

## 3.6 Configuración de Seguridad Adicional

Editar `/etc/mysql/mariadb.conf.d/50-server.cnf`:

```ini
[mysqld]
bind-address = 127.0.0.1
skip-networking
local-infile = 0
```

Reiniciar:
```bash
sudo systemctl restart mariadb
```
