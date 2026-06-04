# 03. Planificación del Proyecto

## 3.1 Fases del Despliegue

El despliegue de la infraestructura LAMP se divide en 5 fases secuenciales, con un tiempo total estimado de **15 días laborables**.

| Fase | Descripción | Duración | Responsable |
|------|-------------|----------|-------------|
| 1 | Análisis y diseño | 2 días | Documentalista de Plataforma |
| 2 | Preparación del servidor base | 2 días | Documentalista de Plataforma |
| 3 | Instalación de servicios LAMP | 4 días | Documentalista de Plataforma |
| 4 | Configuración de seguridad y monitorización | 3 días | Documentalista de Operaciones |
| 5 | Pruebas, documentación final y entrega | 4 días | Ambos |

## 3.2 Diagrama de Gantt

```
Día:         01  02  03  04  05  06  07  08  09  10  11  12  13  14  15
             ├───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
Fase 1:      ████████
Análisis     ████████
Diseño               ████████
                     ████████
Fase 2:                      ████████
Servidor base                ████████
Fase 3:                              ████████████████
Apache                               ████████
PHP                                          ████████
MariaDB                                              ████████
Fase 4:                                                      ████████████
Seguridad/UFW                                                ████████
Monitorización                                                       ████████
Backups                                                              ████████
Fase 5:                                                                      ████████████████
Pruebas                                                                      ████████
Documentación                                                                        ████████
Entrega                                                                                    ████████
```

## 3.3 Hitos del Proyecto

| Hito | Fecha estimada | Entregable |
|------|----------------|------------|
| H1: Diseño aprobado | Día 4 | Documentos 01 y 02 revisados |
| H2: Servidor base listo | Día 6 | Ubuntu instalado y actualizado |
| H3: LAMP operativo | Día 10 | Web y BBDD accesibles |
| H4: Seguridad configurada | Día 13 | Firewall, SSH y backups activos |
| H5: Entrega final | Día 15 | Documentación completa y pruebas OK |

## 3.4 Recursos Necesarios

### Hardware
- 1 servidor físico o VM con mínimo: 2 CPU, 4 GB RAM, 40 GB disco
- 1 máquina de administración para el equipo

### Software
- Ubuntu Server 22.04 LTS
- Apache 2.4.x
- PHP 8.1
- MariaDB 10.6
- Netdata (monitorización)
- UFW (firewall)

### Personal
- 1 Documentalista de Plataforma
- 1 Documentalista de Operaciones
- 1 Responsable de validación (cliente)

## 3.5 Riesgos y Mitigación

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Caída del servidor durante instalación | Media | Alto | Backups automáticos diarios |
| Brecha de seguridad por configuración errónea | Baja | Crítico | Revisión de seguridad en Fase 4 |
| Retraso en la entrega de documentación | Media | Medio | Planificación con margen de 2 días |
| Incompatibilidad de versiones de software | Baja | Medio | Uso de versiones LTS estables |
