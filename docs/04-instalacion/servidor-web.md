# Instalación del Servidor Web y Balanceador (HAProxy)

## Instalación de Apache y PHP

Actualizamos el sistema e instalamos Apache junto con PHP y sus módulos más comunes:

```bash
sudo apt update
sudo apt install apache2 php libapache2-mod-php php-mysql php-curl -y
```

Iniciamos y habilitamos el servicio de Apache para que arranque con el sistema:

```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

Verificamos que el servicio está activo:

```bash
sudo systemctl status apache2
```

## Instalación y Configuración de HAProxy

Para cumplir con el nuevo requisito del cliente, instalamos el balanceador de carga HAProxy delante de Apache:

```bash
sudo apt install haproxy -y
```

Editamos el archivo de configuración `/etc/haproxy/haproxy.cfg` para redirigir el tráfico al servidor web:

```haproxy
frontend http_front
    bind *:80
    default_backend web_servers

backend web_servers
    balance roundrobin
    server web1 127.0.0.1:8080 check
```

*(Nota: En un entorno real, Apache se configuraría para escuchar en el puerto 8080 y HAProxy en el 80).*

Reiniciamos HAProxy para aplicar los cambios:

```bash
sudo systemctl restart haproxy
sudo systemctl enable haproxy
```

## Verificación final

Comprobamos que ambos servicios están corriendo correctamente sin errores:

```bash
sudo systemctl status apache2
sudo systemctl status haproxy
```
