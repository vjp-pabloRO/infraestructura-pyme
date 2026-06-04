# Reflexión del Proyecto

## Conflictos encontrados y cómo los resolvimos

### Conflicto 1: Tabla de versiones en 02-diseno.md (Sesión 2)
- **Causa:** Ambos modificamos la versión de Apache simultáneamente (2.4.60 vs 2.4.59).
- **Resolución:** Usamos `git merge` tradicional. Decidimos mantener la versión más reciente (2.4.60) y añadir la fila de Certbot que propuso el compañero.
- **Aprendizaje:** Es fundamental coordinarse antes de editar la misma sección de un archivo.

### Conflicto 2: Archivo ssh-firewall.md (Sesión 3)
- **Causa:** Ambos añadimos reglas UFW diferentes en el mismo archivo.
- **Resolución:** Usamos `git rebase` para mantener un historial más lineal. Combinamos ambas configuraciones manteniendo las reglas de seguridad de ambos.
- **Aprendizaje:** El rebase es útil para mantener un historial limpio, pero requiere más atención al resolver conflictos.

## Comandos Git más utilizados

| Comando | Uso | Frecuencia |
|---------|-----|------------|
| `git add` | Añadir archivos al staging | Muy alta |
| `git commit` | Guardar cambios con mensaje | Muy alta |
| `git push` | Subir cambios al repositorio remoto | Muy alta |
| `git pull` | Traer cambios del repositorio remoto | Alta |
| `git checkout -b` | Crear y cambiar a nueva rama | Alta |
| `git pull --rebase` | Traer cambios reorganizando historial | Media |
| `git rebase --continue` | Continuar rebase tras resolver conflicto | Baja |

## ¿Qué haríamos diferente en un próximo proyecto?

1. **Comunicación más frecuente:** Antes de editar los mismos archivos, coordinarnos mejor para evitar conflictos innecesarios.

2. **Pull de main más frecuente:** Hacer `git pull origin main` más a menudo para mantener las ramas actualizadas y detectar conflictos antes.

3. **Mensajes de commit más descriptivos:** Ser más específicos en los mensajes de commit para facilitar la trazabilidad de los cambios.

4. **Revisar PRs más a fondo:** Dedicar más tiempo a revisar los Pull Requests del compañero, no solo aprobar por cumplir.

## Experiencia con el intercambio de roles

El intercambio de roles en la Sesión 3 fue muy positivo porque:

- **Ambos tocamos todos los archivos:** No nos limitamos a una parte del proyecto, sino que entendimos toda la infraestructura.
- **Aprendimos a revisar y mejorar el trabajo del otro:** Al revisar los documentos del compañero, detectamos mejoras y aprendimos nuevas formas de documentar.
- **Generó conflictos reales:** El intercambio forzó situaciones de colaboración real, no solo trabajo paralelo.
- **Mejoró la calidad final:** Al tener dos perspectivas sobre cada documento, la documentación final es más completa y robusta.

## Conclusión

Este proyecto nos ha permitido practicar no solo la documentación técnica, sino también el flujo de trabajo colaborativo con Git y GitHub. Los conflictos que surgieron nos enseñaron la importancia de la comunicación y de usar las herramientas adecuadas (merge vs rebase) según el contexto.

La experiencia de trabajar con ramas, Pull Requests, revisiones y resolución de conflictos nos ha preparado para escenarios reales de desarrollo colaborativo en equipos de sistemas.
