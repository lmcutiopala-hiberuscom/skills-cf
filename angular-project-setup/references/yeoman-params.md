# Parámetros del generador Yeoman para proyectos Angular

Tabla completa de las preguntas que realiza el generador `yo krg-angular-project` y cómo responderlas.

> Presiona **Enter** para aceptar el valor por defecto de cualquier pregunta.

| Pregunta | Campo | Valor por defecto | Observaciones |
|----------|-------|------------------|---------------|
| What is the name of the project? | `nameProject` | `kng-base` | El generador añade el sufijo `-web` automáticamente. Si el repositorio se llama `publix-web`, ingresa solo `publix`. |
| What is the group? | `group` | `ec.com.smx.base` | Paquete raíz del proyecto. Ver tabla de grupos en `project-naming-standards/SKILL.md`. |
| What is the code of the system? | `systemCode` | `BASE` | Código del sistema en mayúsculas. |
| What is the context? | `context` | `baseWeb` | Contexto en el que se ejecutará el frontend (ruta base de la aplicación). |
| What is the context of the web services? | `contextBackend` | `baseServices` | Debe coincidir con el contexto configurado en el generador Spring Boot. |
| What is the registry? | `registry` | `docker.krugernetes.com/kruger` | Registro Docker de imágenes. Se recomienda mantener el valor por defecto. |
| What is the namespace? | `namespace` | `base` | Espacio de trabajo en Kubernetes que identifica al proyecto. |
| What is the name of the services folder? | `core` | `core` | Nombre del directorio que contiene los servicios Angular. Se recomienda mantener el valor por defecto (sigue la estructura recomendada por Angular). |
| What is the name of the initial component? | `home` | `home` | Nombre del componente principal de la aplicación. Se recomienda mantener el valor por defecto. |
| What is the name of the constant values folder? | `constants` | `constants` | Nombre del directorio de valores fijos globales. Se recomienda mantener el valor por defecto. |
| What is the name of the models folder? | `shared` | `shared` | Nombre del directorio de estructuras de datos (modelos/interfaces). Se recomienda mantener el valor por defecto. |
| What is the name of the components folder? | `modules` | `modules` | Nombre del directorio de componentes y módulos Angular. |
| What is the realm to use for Keycloak? | `realm` | — | Realm de autenticación: `CFAVORITA-SSO-INTRANET` para proyectos Intranet, `CFAVORITA-PRT` para proyectos MiPortal. |
| What is the clientId to use for Keycloak? | `clientId` | `BASE-WEB` | El `clientId` se debe solicitar su creación con anticipación en: https://favorita.atlassian.net/wiki/spaces/KEY/pages/2556198982 |
| What is the name of the Author? | `author` | — | Nombre completo del desarrollador responsable del proyecto. |
| What is the mail of the Author? | `mail` | — | Correo electrónico del desarrollador responsable. |
| What is the name of the channel for the notifications? | `channelNotification` | `kng-ci` | Canal de Slack al que Jenkins enviará notificaciones durante la construcción del proyecto. |

---

## Referencia de Keycloak

| Tipo de proyecto | Realm |
|-----------------|-------|
| Intranet corporativa | `CFAVORITA-SSO-INTRANET` |
| Portal empleados (MiPortal) | `CFAVORITA-PRT` |
