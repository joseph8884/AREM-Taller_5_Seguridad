# 📋 Evaluación de Seguridad STRIDE - Plataforma EdukIT

## 📆 Sesión de Trabajo
Análisis de riesgos de seguridad: Taller 5 - Evaluación de Seguridad con STRIDE

## 🎯 Objetivo de la Sesión

Evaluar los riesgos de seguridad en la plataforma de educación virtual **EdukIT** utilizando el marco **STRIDE** (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege). El análisis abarca componentes críticos del sistema como autenticación, APIs, bases de datos, sistemas de roles y gestión de logs.

---

## 🔍 Caso de Referencia: EdukIT

**Descripción del sistema:**
EdukIT es una plataforma de educación en línea que ofrece cursos certificados a estudiantes en América Latina. El sistema gestiona:
- Acceso de estudiantes a cursos y materiales educativos
- Publicación de contenidos por parte de docentes
- Procesamiento de pagos y suscripciones
- Almacenamiento de información personal, académica y transaccional
- Control de roles: Estudiante, Docente, Administrador

**Criticidad:** Alta - El sistema gestiona datos sensibles y procesos académicos clave que requieren protección reforzada.

---

## 📊 Análisis STRIDE - Matriz de Evaluación de Amenazas

| ID | Componente / Activo | Tipo STRIDE | Descripción de la Amenaza | Escenario de Ataque | Impacto | Probabilidad | Nivel de Riesgo | Controles Existentes | Mitigación Recomendada | Responsable | Estado |
|:---:|---|---|---|---|---|:---:|:---:|---|---|---|---|
| 1 | Login / Autenticación | Spoofing | Suplantación de estudiante | Uso de credenciales robadas para iniciar sesión | Acceso no autorizado a cursos | Media | Medio | Login con contraseña | Autenticación multifactor (MFA) | Equipo TI | Pendiente |
| 2 | Login / Autenticación | Spoofing | Uso de cuentas compartidas | Estudiantes comparten credenciales entre usuarios | Acceso indebido a contenido | Media | Medio | Política de cuentas | Detección de sesiones múltiples simultáneas | Equipo TI | Pendiente |
| 3 | API de cursos | Tampering | Manipulación de request | Modificar request para acceder a curso sin pagar | Acceso a contenido sin autorización | Media | Medio | Validación básica | Validación backend de permisos | Backend | Pendiente |
| 4 | API de cursos | Tampering | Alteración de parámetros | Cambio de ID de curso en la petición | Acceso a cursos restringidos | Baja | Bajo | Control de rutas | Validación de autorización en cada endpoint | Backend | Pendiente |
| 5 | Sistema de logs | Repudiation | Negación de envío de examen | Estudiante niega haber enviado examen | Conflictos académicos | Media | Medio | Logs básicos | Auditoría completa de eventos con timestamp | TI | Pendiente |
| 6 | Sistema de logs | Repudiation | Negación de actividad | Docente niega haber modificado contenido | Problemas de trazabilidad | Baja | Bajo | Registro de actividad | Logs firmados digitalmente | TI | Pendiente |
| 7 | Base de datos | Information Disclosure | Exposición de datos personales | Acceso indebido a base de datos | Filtración de datos de estudiantes | Media | Alto | Control de acceso | Cifrado de datos en reposo y tránsito | Seguridad | Pendiente |
| 8 | Base de datos | Information Disclosure | Acceso a calificaciones | Usuario accede a notas de otros estudiantes | Violación de privacidad académica | Media | Alto | Roles básicos | Control estricto de roles y permisos | Seguridad | Pendiente |
| 9 | Servidor de cursos | Denial of Service | Saturación del sistema | Alto volumen de solicitudes | Usuarios no pueden acceder al servicio | Media | Medio | Infraestructura básica | Autoescalado y balanceo de carga | Infraestructura | Pendiente |
| 10 | Servidor de cursos | Denial of Service | Ataque de tráfico | Bots generan tráfico excesivo | Interrupción del servicio educativo | Baja | Medio | Firewall | Protección anti-DDoS | Infraestructura | Pendiente |
| 11 | Sistema de roles | Elevation of Privilege | Escalada de privilegios | Estudiante modifica token de acceso | Acceso a funciones administrativas | Baja | Alto | Roles definidos | Validación de permisos en backend | Backend | Pendiente |
| 12 | Sistema de roles | Elevation of Privilege | Asignación indebida de rol | Error en sistema asigna rol administrador | Control total del sistema comprometido | Baja | Alto | Gestión manual de roles | Revisión automática de permisos | Seguridad | Pendiente |

---

## 🎯 Hallazgos Clave

### Amenazas Críticas (Nivel Alto)
- **Información Disclosure (ID 7, 8):** Riesgo elevado de filtración de datos personales y académicos
- **Elevation of Privilege (ID 11, 12):** Vulnerabilidades en el sistema de roles permiten escalada de privilegios

### Amenazas Moderadas (Nivel Medio)
- **Spoofing (ID 1, 2):** Suplantación de identidad mediante robo de credenciales
- **Tampering (ID 3):** Manipulación de requests para acceso no autorizado
- **Denial of Service (ID 9, 10):** Saturación del sistema afectando disponibilidad

### Recomendaciones Prioritarias
1. Implementar autenticación multifactor en login
2. Reforzar controles de autorización en backend
3. Cifrar datos sensibles en base de datos
4. Implementar detección de sesiones múltiples
5. Establecer protección anti-DDoS

---

## 📌 Conclusiones

El análisis STRIDE de EdukIT identifica **12 amenazas potenciales** distribuidas en **6 categorías de riesgo**. El sistema requiere mejoras significativas en:
- Control de identidad y autenticación
- Protección de datos en reposo y tránsito
- Validación y autorización en backend
- Detección y mitigación de ataques

La implementación de las mitigaciones recomendadas elevará el nivel de seguridad a estándares aceptables para una plataforma educativa que gestiona información sensible.


