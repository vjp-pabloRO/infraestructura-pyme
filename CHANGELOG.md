# Changelog

Todos los cambios notables en este proyecto serán documentados en este archivo.

El formato está basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/).

## [1.0.0] - 2026-06-05

### Añadido
- Documentación completa del despliegue de infraestructura LAMP
- Análisis de requisitos (`docs/01-analisis.md`)
- Diseño de infraestructura (`docs/02-diseno.md`)
- Planificación del proyecto (`docs/03-planificacion.md`)
- Guía de instalación de Apache, PHP y HAProxy (`docs/04-instalacion/servidor-web.md`)
- Guía de instalación de MariaDB (`docs/04-instalacion/base-de-datos.md`)
- Configuración de SSH y Firewall (`docs/04-instalacion/ssh-firewall.md`)
- Monitorización con Netdata (`docs/04-instalacion/monitorizacion.md`)
- Estrategia de backups (`docs/04-instalacion/backups.md`)
- Plan de operación y mantenimiento (`docs/05-operacion.md`)
- Plan de recuperación ante desastres (`docs/06-recuperacion.md`)
- Configuración de HAProxy como balanceador de carga
- Archivo de reflexión del proyecto (`REVISION.md`)

### Cambiado
- Versión de Apache actualizada a 2.4.60
- Añadido Certbot para certificados SSL/TLS
- Añadido HAProxy 2.6 para balanceo de carga

### Sesiones completadas
- **Sesión 1**: Creación del repositorio, estructura inicial y primeros PRs
- **Sesión 2**: Revisión cruzada, merges y resolución de conflicto en `02-diseno.md`
- **Sesión 3**: Intercambio de roles, nuevos documentos y conflicto en `ssh-firewall.md`
- **Sesión 4**: Cambio de alcance (HAProxy), pulido final y release v1.0

## [0.1.0] - 2026-06-04

### Añadido
- Estructura inicial del proyecto
- README.md con descripción del proyecto
- Carpetas y archivos vacíos para la documentación
