# Instalación del Servidor Web (Apache + PHP)

## 2.1 Instalación de Apache

```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
```

Verificación:
```bash
sudo systemctl status apache2
curl -I http://localhost
```

## 2.2 Instalación de PHP 8.1

```bash
sudo apt install php libapache2-mod-php php-mysql php-curl php-gd php-mbstring -y
sudo systemctl restart apache2
```

Verificación:
```bash
php -v
echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
```
⚠️ **Importante**: Eliminar `info.php` después de verificar por seguridad:
```bash
sudo rm /var/www/html/info.php
```

## 2.3 Configuración de VirtualHosts

Archivo `/etc/apache2/sites-available/web.conf`:

```apache
<VirtualHost *:80>
    ServerName www.pyme.local
    DocumentRoot /var/www/html/web
    
    <Directory /var/www/html/web>
        AllowOverride All
        Require all granted
    </Directory>
    
    ErrorLog ${APACHE_LOG_DIR}/web_error.log
    CustomLog ${APACHE_LOG_DIR}/web_access.log combined
</VirtualHost>

<VirtualHost *:80>
    ServerName gestion.pyme.local
    DocumentRoot /var/www/html/gestion
    
    <Directory /var/www/html/gestion>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Activación:
```bash
sudo a2ensite web.conf gestion.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
```

## 2.4 Estructura de Directorios

```
/var/www/
├── html/
│   ├── web/          # Web pública
│   └── gestion/      # Panel interno
└── backups/          # Copias de seguridad
```

Permisos recomendados:
```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```
