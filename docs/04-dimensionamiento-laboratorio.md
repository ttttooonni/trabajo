# 04 — Dimensionamiento del laboratorio

## 1. Equipo anfitrión conocido

| Recurso | Especificación |
|---|---|
| Sistema operativo | Windows 11 |
| Memoria RAM | 16 GB |
| Procesador | Intel Core i5 (generación y número de núcleos pendientes) |
| Almacenamiento | SSD 512 GB |

La generación exacta del procesador, el número de núcleos/hilos y el espacio libre del SSD deberán comprobarse antes de fijar los ajustes definitivos.

## 2. Estrategia

Se utilizará una sola máquina virtual principal Ubuntu Server y se desplegarán los servicios auxiliares mediante Docker Compose. Cisco Packet Tracer se utilizará para la simulación de red.

No se asignará memoria adicional a Docker por separado: los contenedores consumen RAM dentro de la memoria asignada a la máquina virtual Ubuntu.

## 3. Recursos iniciales

### Máquina virtual Ubuntu Server

| Parámetro | Valor inicial |
|---|---|
| Sistema | Ubuntu Server 24.04 LTS |
| RAM | 4 GB |
| CPU virtual | 2 vCPU |
| Disco virtual | 60 GB, asignación dinámica |
| Red | NAT para salida a Internet y red interna para laboratorio |
| Interfaz gráfica | No instalar |
| Instantánea | Crear tras instalación y actualización inicial |

La asignación de 2 vCPU es provisional y se revisará cuando se conozca el modelo exacto del i5 y su número de núcleos.

### Memoria del equipo

Orientación de uso, no una reserva rígida:

- Windows 11 y procesos del anfitrión: aproximadamente 5–7 GB.
- Ubuntu Server: 4 GB asignados a la VM, incluyendo Docker.
- Margen restante: mantener varios GB disponibles para evitar paginación excesiva.
- Packet Tracer: carga variable y normalmente ligera; cerrar aplicaciones no necesarias durante pruebas intensivas.

Si Windows consume más memoria de la prevista, reducir temporalmente la RAM de Ubuntu a 3 GB o apagar la VM al utilizar otras herramientas exigentes.

## 4. Almacenamiento

El SSD de 512 GB es suficiente para comenzar, siempre que exista espacio libre adecuado.

Plan inicial:

- Disco virtual Ubuntu: máximo de 60 GB, dinámico.
- ISO de instalación: eliminarla del almacenamiento de trabajo cuando ya no sea necesaria.
- Copias de seguridad: guardar fuera del disco virtual y, cuando sea posible, en un segundo destino.
- Instantáneas: utilizarlas de forma puntual; no sustituyen a las copias de seguridad y pueden consumir espacio adicional.

Antes de crear la VM, comprobar el espacio libre real en Windows. Se recomienda disponer de al menos 100 GB libres para trabajar con comodidad y conservar margen para snapshots, actualizaciones y copias.

## 5. Servicios previstos

Primera fase, dentro de Docker Compose:

- Nginx para servir la PWA o actuar como proxy según el modo de compilación validado.
- Uptime Kuma para comprobación de disponibilidad.
- Restic ejecutado mediante tareas programadas para copias de los elementos definidos.

No se desplegarán inicialmente Grafana, Prometheus, bases de datos adicionales ni varias máquinas virtuales. Se añadirán solo si los requisitos académicos y los recursos lo justifican.

## 6. Comprobaciones previas en Windows

1. Consultar el modelo exacto del procesador en Administrador de tareas > Rendimiento > CPU o con `msinfo32`.
2. Comprobar memoria disponible y aplicaciones de inicio.
3. Comprobar espacio libre del SSD.
4. Verificar que Intel VT-x está habilitado en BIOS/UEFI.
5. Comprobar el estado de virtualización en Administrador de tareas > Rendimiento > CPU.
6. Instalar una versión actual de VirtualBox compatible con Windows 11.
7. Comprobar si Hyper-V, Plataforma de máquina virtual, WSL2 o Integridad de memoria afectan al rendimiento de VirtualBox. No desactivar funciones de seguridad de Windows sin una necesidad demostrada.

## 7. Criterios de aceptación

- La máquina virtual arranca y se apaga correctamente.
- Ubuntu Server dispone de conectividad de salida.
- El anfitrión puede acceder a los servicios del laboratorio mediante una configuración de red documentada.
- La VM no provoca uso sostenido de memoria virtual o bloqueos del anfitrión.
- Se documentan consumo de RAM, CPU y disco durante las pruebas.
- Se conserva una copia de seguridad independiente de la VM y sus configuraciones relevantes.

## 8. Datos pendientes

- Modelo exacto y generación del Intel Core i5.
- Número de núcleos e hilos.
- Espacio libre real del SSD.
- Versión exacta de Windows 11.
- Estado de Intel VT-x y configuración de virtualización de Windows.

**Estado:** dimensionamiento inicial. Los valores se validarán con una prueba de instalación y carga antes de considerarse definitivos.
