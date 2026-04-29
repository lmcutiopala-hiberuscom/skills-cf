# Skill: Configuración de Proyectos Angular

## Descripción
Este skill guía la creación de proyectos Angular frontend utilizando el generador Yeoman interno y los estándares de la compañía.

## Cuándo usarlo
- Al iniciar un nuevo proyecto frontend Angular.
- Al verificar que el entorno de desarrollo cumple los requisitos mínimos.
- Al responder las preguntas del generador Yeoman para personalizar el proyecto.

---

## 1. Requisitos previos

Antes de crear un proyecto, verifica que tu entorno cumpla con lo siguiente:

| Herramienta | Versión requerida | Comando de verificación |
|------------|------------------|------------------------|
| Node.js | 14.15.0 | `node -v` |
| npm | 6.14.8 | `npm -v` |
| Angular CLI | 13 | `ng version` |
| Yeoman | 4.3.0 | `yo --version` |

### Instalación de Angular CLI
```bash
npm i -g @angular/cli@13
```

### Configurar el registro privado npm
```bash
npm set registry https://cf1nxs.cfavorita.net/repository/npm-all/
```

---

## 2. Generadores disponibles

| Generador | Uso |
|-----------|-----|
| `generator-krg-angular-project` | Proyectos legacy Angular |
| `@krugercorp/generator-krg-angular-20-project` v1.7.2 | Proyectos Angular modernos |

---

## 3. Verificación y actualización del generador

Antes de generar un nuevo proyecto, asegúrate de tener la última versión del generador:

```bash
# Consultar la última versión publicada en el repositorio
npm view generator-krg-angular-project version

# Consultar la versión instalada localmente
npm list generator-krg-angular-project version -g

# Actualizar a la última versión disponible
npm install -g generator-krg-angular-project@latest
```

---

## 4. Pasos para crear el proyecto

1. Consulta [`../project-naming-standards/SKILL.md`](../project-naming-standards/SKILL.md) para definir el nombre del proyecto siguiendo los estándares.
2. Crea el directorio del proyecto con el nombre estándar (sufijo `-web`):
   ```bash
   mkdir {nombre-sistema}-web
   ```
3. Ingresa al directorio:
   ```bash
   cd {nombre-sistema}-web
   ```
4. Ejecuta el generador Yeoman:
   ```bash
   yo krg-angular-project
   ```
5. Responde las preguntas del generador (ver sección siguiente). Presiona **Enter** para aceptar el valor por defecto.

---

## 5. Parámetros del generador Yeoman

Consulta la tabla completa de parámetros en [`references/yeoman-params.md`](references/yeoman-params.md).

A continuación se muestra un resumen de los parámetros más importantes:

| Pregunta | Campo | Valor por defecto | Notas clave |
|----------|-------|------------------|-------------|
| What is the name of the project? | `nameProject` | `kng-base` | **No incluir** el sufijo `-web`; el generador lo añade automáticamente |
| What is the group? | `group` | `ec.com.smx.base` | Ver estándares de grupo en `project-naming-standards` |
| What is the code of the system? | `systemCode` | `BASE` | Código en mayúsculas |
| What is the context? | `context` | `baseWeb` | Contexto de ejecución del frontend |
| What is the context of the web services? | `contextBackend` | `baseServices` | Debe coincidir con el contexto del proyecto Spring Boot |
| What is the realm to use for Keycloak? | `realm` | — | `CFAVORITA-SSO-INTRANET` (Intranet) o `CFAVORITA-PRT` (MiPortal) |
| What is the clientId to use for Keycloak? | `clientId` | `BASE-WEB` | Solicitar creación previa en: https://favorita.atlassian.net/wiki/spaces/KEY/pages/2556198982 |
| What is the name of the Author? | `author` | — | Nombre del desarrollador responsable |
| What is the mail of the Author? | `mail` | — | Correo del desarrollador responsable |
| What is the name of the channel for the notifications? | `channelNotification` | `kng-ci` | Canal de Slack para notificaciones de Jenkins |

---

## Referencias cruzadas
- Nomenclatura de repositorios y artefactos: [`../project-naming-standards/SKILL.md`](../project-naming-standards/SKILL.md)
- Creación de proyectos backend: [`../springboot-project-setup/SKILL.md`](../springboot-project-setup/SKILL.md)
