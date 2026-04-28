# Skill: Configuración de Proyectos Spring Boot

## Descripción
Este skill guía la creación y configuración inicial de proyectos backend Spring Boot utilizando los generadores Yeoman internos y los estándares de la compañía.

## Cuándo usarlo
- Al iniciar un nuevo proyecto backend Java/Spring Boot.
- Al configurar los archivos generados para adaptarlos al sistema y entorno concreto.
- Al verificar que el entorno de desarrollo cumple los requisitos mínimos.

---

## 1. Requisitos previos

| Herramienta | Versión requerida | Comando de verificación |
|------------|------------------|------------------------|
| Java | 21 | `java -version` |
| Gradle | 8.7 | `gradle -v` |
| Node.js | 20.14.0 | `node -v` |
| Yeoman | 4.3.0 | `yo --version` |

### Configurar el registro privado npm
```bash
npm set registry https://cf1nxs.cfavorita.net/repository/npm-all/
```

---

## 2. Generadores disponibles

| Generador | Versión | Uso |
|-----------|---------|-----|
| `@krugercorp/generator-krg-springboot-4.0-project` | 1.7.0 | Proyectos Spring Boot estándar |
| `@krugercorp/generator-krg-cronjob-4.0-project` | 1.7.0 | Proyectos CronJob (tareas programadas K8s) |

---

## 3. Estructura de módulos generada

El generador crea los siguientes módulos dentro del proyecto:

| Módulo | Sufijo | Descripción |
|--------|--------|-------------|
| Servicios web | `-services` | Controladores REST y configuración de la aplicación |
| Implementación de negocio | `-core` | Lógica de negocio e implementaciones |
| Contratos/interfaces | `-client` | DTOs y contratos de API |
| Value Objects | `-vo` | Objetos de valor compartidos |

---

## 4. Archivos a personalizar tras la generación

Después de ejecutar el generador, debes personalizar los siguientes archivos. Consulta [`references/files-to-customize.md`](references/files-to-customize.md) para la lista completa.

### 4.1 Prefijo del sistema
Reemplaza el prefijo por defecto (`base`) en los siguientes archivos:

- `sonar-project.properties`
- `settings.gradle`
- `ci/helm/values.yaml`
- `ci/helm/Chart.yaml`
- `ci/docker/DockerfileCI`
- `**/build.gradle` (todos los módulos)

### 4.2 Contexto de la aplicación
El contexto por defecto es `baseServices`. Reemplázalo en:

- `application.yaml`
- `application-CONSOLA.yaml`
- `ci/helm/questions.yaml`
- `ci/helm/values.yaml`

### 4.3 Grupo (paquete Java)
El grupo por defecto es `ec.com.smx.base`. Reemplázalo en:

- `build.gradle` (raíz y módulos)
- `ci/README.md`
- `ci/helm/values.yaml`
- Todos los archivos `.java` en `client/`, `core/`, `services/` y `vo/`
- Estructura de carpetas: `ec/com/smx/base/` → `ec/com/smx/{sistema}/`

### 4.4 Configuración Keycloak
Actualiza el campo `resource` en los perfiles de entorno:

- `application-CONSOLA.yaml`
- `application-PRUEBAS.yaml`
- `application-PRODUCCION.yaml`

### 4.5 CI/CD
- `Jenkinsfile` → campo `namespace`
- `ci/helm/values.yaml` → esquema de base de datos
- `ci/docker/DockerfileCI` → responsable del proyecto
- `ci/helm/Chart.yaml` → responsable del proyecto

---

## 5. Consejo para refactorizar con IntelliJ IDEA

Para reemplazar el prefijo o el grupo de forma masiva en todo el proyecto:

1. Abre **Refactor → Rename** sobre el término a reemplazar.
2. Activa la opción **"In Whole Project"**.
3. Marca **"Search for text occurrences"**.
4. Selecciona el scope **"All places"**.

---

## 6. Compilar y ejecutar

Consulta [`references/build-and-run.md`](references/build-and-run.md) para los comandos completos.

### Compilar
```bash
# Windows
gradlew clean build

# Linux / macOS
./gradlew clean build
```

### Ejecutar
```bash
# Configurar perfil activo (Windows)
setx SPRING_PROFILES_ACTIVE "CONSOLA"

# Navegar a los artefactos compilados
cd {prefijo}-services/build/libs/

# Iniciar la aplicación
java -jar {prefijo}-services-1.0.0-SNAPSHOT.jar
```

### Verificar que la aplicación está en ejecución
```
GET http://localhost:8080/{contexto}/actuator/health
```

---

## 7. Documentación de la API

| Recurso | URL |
|---------|-----|
| Actuator (salud y métricas) | `http://localhost:8080/{contexto}/actuator` |
| OpenAPI JSON | `http://localhost:8080/{contexto}/v3/api-docs` |
| Swagger UI | `http://localhost:8080/{contexto}/swagger-ui.html` |

---

## 8. Obtener token OAuth2 / Keycloak

Para autenticar peticiones en entornos con Keycloak:

```http
POST /auth/realms/CFAVORITA-SSO-INTRANET/protocol/openid-connect/token
Content-Type: application/x-www-form-urlencoded

username={usuario}&password={contraseña}&grant_type=password&client_id={client_id}
```

Usa el `access_token` de la respuesta como cabecera de autorización:
```
Authorization: Bearer {access_token}
```

---

## Referencias cruzadas
- Nomenclatura de repositorios y artefactos: [`../project-naming-standards/SKILL.md`](../project-naming-standards/SKILL.md)
- Creación de proyectos frontend: [`../angular-project-setup/SKILL.md`](../angular-project-setup/SKILL.md)
