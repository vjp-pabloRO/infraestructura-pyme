# Despliegue de Infraestructura LAMP para PYME

Documentación técnica colaborativa para el despliegue de una infraestructura web corporativa con balanceador de carga, monitorización y copias de seguridad.

## 👥 Equipo
- **Miembro A:** Pablo Recio Oliva
- **Miembro B:** Diego Recuero Barrado

## 📁 Documentación
Toda la documentación técnica se encuentra en la carpeta `docs/`:

- [01. Análisis de Requisitos](docs/01-analisis.md)
- [02. Diseño de Infraestructura](docs/02-diseno.md)
- [03. Planificación](docs/03-planificacion.md)
- **Instalación:**
  - [Servidor Web y HAProxy](docs/04-instalacion/servidor-web.md)
  - [Base de Datos](docs/04-instalacion/base-de-datos.md)
  - [SSH y Firewall](docs/04-instalacion/ssh-firewall.md)
  - [Monitorización](docs/04-instalacion/monitorizacion.md)
  - [Backups](docs/04-instalacion/backups.md)
- [05. Plan de Operación](docs/05-operacion.md)
- [06. Plan de Recuperación](docs/06-recuperacion.md)

## 🚀 Tecnologías
- **Sistema Operativo:** Ubuntu Server 22.04 LTS
- **Servidor Web:** Apache 2.4 + PHP 8.1
- **Base de Datos:** MariaDB 10.6
- **Balanceador:** HAProxy 2.6
- **Seguridad:** UFW, SSH endurecido, Certbot
- **Monitorización:** Netdata

## 📊 Estado del Proyecto
- [x] Sesión 1: Estructura y primeras ramas
- [x] Sesión 2: Revisión cruzada y conflicto (merge)
- [x] Sesión 3: Intercambio de roles y conflicto (rebase)
- [x] Sesión 4: HAProxy, Release v1.0 y Reflexión

## 📝 Archivos adicionales
- [CHANGELOG.md](CHANGELOG.md) - Historial de cambios
- [REVISION.md](REVISION.md) - Reflexión final del equipo
- [tareas.md](tareas.md) - Lista de tareas pendientes
