# 03 — Arquitectura inicial

## 1. Principios de diseño

- Separar la aplicación existente de la infraestructura del PFC.
- Empezar con una arquitectura pequeña y ampliarla solo si las pruebas lo justifican.
- Mantener los servicios dentro de una red de laboratorio durante el desarrollo.
- Aplicar mínimo privilegio y exposición mínima de puertos.
- Documentar y versionar los cambios.
- Probar las copias mediante restauraciones reales.
- No almacenar datos apícolas de usuarios en el servidor en esta fase.

## 2. Vista lógica

```text
                 CLIENTE DE PRUEBA
              navegador móvil/ordenador
                         |
                         |
                RED DE LABORATORIO
                         |
             Router / switch simulado
                         |
             +-----------+-----------+
             |           |           |
          VLAN 10     VLAN 20     VLAN 30
          Usuarios    Servidores  Administración
             |           |           |
             |      Ubuntu Server    |
             |           |           |
             +------ HTTPS/web       |
                         |
                  Docker Compose
                         |
                   Nginx / PWA
                         |
                 Monitorización
                         |
               Copias de configuración
```

El diagrama es conceptual. La implementación final dependerá de las capacidades del laboratorio y de la simulación de red.

## 3. Plan de direccionamiento provisional

| VLAN | Nombre | Red | Uso |
|---|---|---|---|
| 10 | Usuarios | 192.168.10.0/24 | Clientes de prueba |
| 20 | Servidores | 192.168.20.0/24 | Ubuntu Server y servicios |
| 30 | Administración | 192.168.30.0/24 | Gestión del servidor y equipos de administración |

Las direcciones, puertas de enlace, rangos DHCP y reglas ACL se concretarán en el diseño de red. No se debe asumir que estas VLAN ya están configuradas.

## 4. Componentes previstos

### Host de virtualización

VirtualBox sobre el equipo disponible. Se utilizará una máquina virtual Ubuntu Server como servidor principal, evitando ejecutar múltiples máquinas pesadas simultáneamente.

### Sistema operativo

Ubuntu Server LTS, con instalación mínima, actualizaciones, usuarios administrativos nominativos, SSH restringido y firewall.

### Despliegue web

Docker Compose gestionará los servicios del laboratorio. Nginx servirá la versión estática de la PWA cuando el modo de compilación y los requisitos de la aplicación lo permitan.

**Nota técnica:** antes de fijar el método de despliegue se verificará el proceso de compilación actual de Mi Apiario. Si la versión elegida requiere runtime de servidor, se documentará y probará ese requisito en lugar de asumir que basta con servir archivos estáticos.

### Seguridad

- UFW para filtrado local.
- SSH con autenticación por clave cuando sea posible.
- Fail2ban si las pruebas y el entorno justifican su instalación.
- Actualizaciones de seguridad.
- Secretos fuera del repositorio.
- No publicar puertos administrativos en Internet.

### Monitorización

Uptime Kuma para comprobar disponibilidad HTTP y estado de servicios. Se valorarán métricas de sistema adicionales solo si caben en los recursos disponibles.

### Copias

Restic para respaldar configuraciones, archivos de despliegue y documentación operativa seleccionada. El repositorio de copias tendrá destino separado del directorio de trabajo. Se probará la restauración.

Las copias de infraestructura no sustituyen las exportaciones locales de datos de los usuarios de Mi Apiario.

## 5. Flujos de red previstos

| Origen | Destino | Servicio | Política inicial |
|---|---|---|---|
| Usuarios | Servidor web | HTTPS | Permitir |
| Administración | Ubuntu Server | SSH | Permitir |
| Usuarios | Administración | SSH/gestión | Denegar |
| Internet | SSH del servidor | SSH | Denegar en el laboratorio |
| Monitorización | Servicios supervisados | HTTP/HTTPS o agente | Permitir solo lo necesario |

Las reglas definitivas se traducirán a ACL y firewall y se validarán con pruebas.

## 6. Decisiones pendientes

- Confirmar el hardware y los recursos de RAM/CPU.
- Verificar la versión y el modo de compilación de Mi Apiario.
- Elegir red interna, NAT o red puente según el laboratorio.
- Definir si DNS y DHCP se simulan en Packet Tracer o se despliegan realmente.
- Determinar el destino externo de las copias.
- Confirmar requisitos de Digitech y aprobación del tutor.

## 7. Estado

Documento de diseño preliminar. No representa una infraestructura ya desplegada ni una prueba de seguridad realizada.
