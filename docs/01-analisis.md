# 01. Análisis de Requisitos

## 1.1 Contexto del Proyecto
La PYME cliente necesita desplegar su primera presencia web corporativa junto con un sistema de gestión interna. El objetivo es centralizar la información de clientes, facturación básica y catálogo de productos/servicios. Se actuará como departamento de sistemas externo, planificando una infraestructura segura, mantenible y documentada.

## 1.2 Requisitos Funcionales
- **Servidor Web**: Apache con soporte PHP para alojar la web pública y el panel de gestión interno.
- **Base de Datos**: MySQL/MariaDB con dos bases independientes:
  - `web_db`: Contenido dinámico de la web.
  - `gestion_db`: Datos de clientes, facturas y stock.
- **Acceso Remoto**: SSH seguro para administración, restringido a IPs de confianza.
- **Monitorización**: Herramienta ligera para visualizar estado de servicios, recursos y alertas básicas.
- **Copias de Seguridad**: Automatización de backups de BBDD y archivos web con rotación y verificación.

## 1.3 Requisitos No Funcionales
- **Disponibilidad**: 99% en horario comercial (08:00–18:00).
- **Seguridad**: Firewall restrictivo, actualizaciones automáticas de seguridad, aislamiento de servicios, cifrado TLS.
- **Mantenibilidad**: Documentación clara, estructura modular, scripts de mantenimiento automatizados.
- **Escalabilidad**: Diseño preparado para añadir balanceador de carga o réplica de BBDD en fases futuras.

## 1.4 Restricciones
- Presupuesto ajustado → soluciones 100% Open Source.
- Hardware único: 1 servidor físico/virtual con Ubuntu Server 22.04 LTS.
- Personal técnico limitado → prioridad a la automatización y documentación operativa.
- Cumplimiento básico de LOPD/RGPD → acceso restringido, backups verificados, trazabilidad de cambios.