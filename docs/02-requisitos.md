# 02 — Requisitos y criterios de aceptación

## 1. Requisitos funcionales

| ID | Requisito | Criterio de aceptación |
|---|---|---|
| RF-01 | Alojar una versión de Mi Apiario | La página se sirve desde el servidor independiente en la red de laboratorio |
| RF-02 | Administrar el servidor remotamente | Acceso SSH permitido solo desde la red de administración |
| RF-03 | Separar redes por función | La topología representa usuarios, servidores y administración |
| RF-04 | Controlar comunicaciones | Las reglas permiten solo los flujos documentados |
| RF-05 | Supervisar servicios | El panel identifica disponibilidad o caída del servicio web |
| RF-06 | Realizar copias de infraestructura | Se genera una copia verificable de los elementos definidos |
| RF-07 | Restaurar una copia | Se demuestra una restauración en un entorno de prueba |
| RF-08 | Automatizar tareas | Los scripts tienen instrucciones, validaciones y registro de ejecución |

## 2. Requisitos no funcionales

- **Seguridad:** mínimo privilegio, acceso administrativo restringido y servicios no necesarios deshabilitados.
- **Integridad:** no modificar los datos locales ni las copias de Mi Apiario.
- **Reproducibilidad:** documentar versiones, configuración y pasos de despliegue.
- **Mantenibilidad:** separar configuración, scripts, documentación y pruebas.
- **Coste:** priorizar herramientas gratuitas y software libre.
- **Viabilidad:** ajustar el número de máquinas virtuales a los recursos reales del equipo.
- **Privacidad:** no incluir credenciales, tokens, claves privadas ni datos personales en Git.

## 3. Requisitos de laboratorio pendientes de confirmar

- Equipo anfitrión, procesador, RAM y almacenamiento disponibles.
- Versión del sistema operativo anfitrión.
- Versión de VirtualBox.
- Espacio libre para máquinas virtuales y copias.
- Posibilidad de utilizar un segundo equipo o almacenamiento externo.
- Requisitos académicos y calendario de Digitech.

## 4. Criterios de aceptación técnica

El proyecto se considerará técnicamente demostrado cuando existan evidencias reproducibles de:

1. Arranque correcto del servidor.
2. Conectividad conforme al diseño.
3. Acceso web a la aplicación desde un cliente de laboratorio.
4. Acceso SSH limitado a administración.
5. Bloqueo de conexiones no autorizadas definidas en el plan.
6. Estado del servicio visible en la herramienta de monitorización.
7. Ejecución de una copia de seguridad.
8. Restauración de esa copia en un destino de prueba.
9. Ejecución correcta de los scripts documentados.
10. Ausencia de secretos y datos sensibles en el repositorio.

## 5. Evidencias

Cada prueba deberá registrar:

- Identificador y objetivo.
- Entorno y versiones.
- Procedimiento.
- Resultado esperado.
- Resultado obtenido.
- Captura o salida de consola.
- Fecha de ejecución.
- Incidencias y resolución.

No se marcará ningún requisito como cumplido hasta que exista evidencia.
