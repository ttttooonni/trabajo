# Trabajo — Proyecto Fin de Ciclo ASIR

**Título provisional:** Diseño e implantación de una infraestructura informática segura para alojar y administrar Mi Apiario.

Este repositorio contiene el trabajo de infraestructura del PFC del ciclo de **Administración de Sistemas Informáticos en Red (ASIR)**. Se mantendrá separado del repositorio de la aplicación Mi Apiario.

## Objetivo

Diseñar, desplegar, administrar, proteger, monitorizar y documentar una infraestructura reproducible para publicar la PWA Mi Apiario, utilizando tecnologías y procedimientos propios de la administración de sistemas.

## Alcance inicial

- Diseño lógico de red y direccionamiento.
- Simulación de VLAN, routing y ACL con Cisco Packet Tracer.
- Instalación y administración de Ubuntu Server.
- Despliegue web independiente mediante Docker Compose y Nginx.
- Configuración de acceso administrativo seguro y firewall.
- Monitorización de disponibilidad y servicios.
- Copias de seguridad de la infraestructura y pruebas de restauración.
- Automatización mediante Bash.
- Documentación, pruebas y memoria del proyecto.

## Principio de separación y protección de datos

- El repositorio original de Mi Apiario no se modifica como parte de este trabajo.
- La aplicación conserva su arquitectura y su almacenamiento local.
- No se implementará sincronización centralizada de datos apícolas en el alcance inicial.
- Las copias de infraestructura no se considerarán copias de los datos locales de los usuarios.
- Toda ampliación que afecte a datos deberá diseñarse con migración, pruebas y recuperación verificable.

## Tecnologías previstas

| Área | Tecnología |
|---|---|
| Sistema operativo | Ubuntu Server |
| Laboratorio | VirtualBox |
| Simulación de red | Cisco Packet Tracer |
| Contenedores | Docker y Docker Compose |
| Servidor web | Nginx |
| Seguridad | UFW, SSH y Fail2ban |
| Monitorización | Uptime Kuma; métricas adicionales si son viables |
| Copias | Restic |
| Automatización | Bash |
| Control de versiones | Git y GitHub |

Las tecnologías son una propuesta inicial. Se confirmarán según los requisitos oficiales de Digitech, los recursos disponibles y las pruebas realizadas.

## Estructura

```text
.
├── README.md
├── docs/
│   ├── 01-propuesta.md
│   ├── 02-requisitos.md
│   └── 03-arquitectura.md
├── infrastructure/
│   ├── docker/
│   ├── nginx/
│   └── monitoring/
├── network/
│   ├── diagrams/
│   └── packet-tracer/
├── scripts/
│   ├── install/
│   ├── backup/
│   └── maintenance/
├── security/
└── tests/
```

## Estado del proyecto

**Fase actual:** definición y diseño inicial.  
**No se considera todavía desplegada ni validada ninguna infraestructura.**

## Próximos hitos

1. Confirmar con el tutor los criterios y resultados de aprendizaje exigidos.
2. Inventariar el equipo disponible y dimensionar el laboratorio.
3. Aprobar el diseño de red y arquitectura.
4. Desplegar el servidor base.
5. Implementar servicios, seguridad, monitorización y copias.
6. Ejecutar pruebas y documentar evidencias.
7. Preparar memoria y defensa.

## Repositorios relacionados

- Aplicación Mi Apiario: https://github.com/ttttooonni/mi-apiario

## Autoría académica

Proyecto personal de fin de ciclo. El alcance y la memoria definitivos quedarán sujetos a la aprobación del centro y del tutor.
