# Monitorización del Sistema

## Herramienta Seleccionada: Netdata

Netdata es una herramienta de monitorización en tiempo real, ligera y de código abierto, ideal para nuestro servidor Ubuntu sin consumir recursos excesivos.

### Instalación

Ejecutar el siguiente script oficial como root o con sudo:

```bash
wget -O /tmp/netdata-kickstart.sh https://my-netdata.io/kickstart.sh && /bin/bash /tmp/netdata-kickstart.sh
```

### Métricas a Monitorizar

- **CPU**: Uso por núcleo y *load average*.
- **RAM**: Memoria utilizada, caché y *swap*.
- **Disco**: Espacio libre, uso de inodos y operaciones de I/O.
- **Red**: Tráfico entrante y saliente por interfaz.
- **Servicios**: Estado de los demonios de Apache, MySQL/MariaDB y SSH.

### Acceso Seguro

Por seguridad, el puerto de Netdata (`19999`) **no** está expuesto a internet en el firewall (UFW). El acceso se realiza mediante túnel SSH desde el equipo del administrador:

```bash
ssh -L 19999:localhost:19999 usuario@192.168.1.100
```

Una vez establecido el túnel, acceder vía navegador a: `http://localhost:19999`

### Alertas Configuradas

El sistema está preconfigurado para notificar ante los siguientes umbrales críticos:
- Uso de disco > 90%
- Uso de RAM > 95%
- Caída del servicio Apache o MySQL