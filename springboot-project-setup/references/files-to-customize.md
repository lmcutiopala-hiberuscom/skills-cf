# Archivos a personalizar tras generar un proyecto Spring Boot

Después de ejecutar el generador Yeoman, los siguientes archivos contienen valores por defecto que deben reemplazarse por los valores específicos del sistema que estás creando.

---

## Prefijo del sistema

El generador usa `base` como prefijo por defecto. Reemplázalo por el nombre corto de tu sistema.

| Archivo | Qué reemplazar |
|---------|---------------|
| `sonar-project.properties` | `base` → `{prefijo}` |
| `settings.gradle` | `base` → `{prefijo}` |
| `ci/helm/values.yaml` | `base` → `{prefijo}` |
| `ci/helm/Chart.yaml` | `base` → `{prefijo}` |
| `ci/docker/DockerfileCI` | `base` → `{prefijo}` |
| `**/build.gradle` (todos los módulos) | `base` → `{prefijo}` |

---

## Contexto de la aplicación

El contexto por defecto es `baseServices`. Reemplázalo por el contexto real del sistema.

| Archivo | Campo / Clave |
|---------|--------------|
| `application.yaml` | `server.servlet.context-path` o similar |
| `application-CONSOLA.yaml` | contexto de la aplicación |
| `ci/helm/questions.yaml` | parámetro de contexto |
| `ci/helm/values.yaml` | parámetro de contexto |

---

## Grupo (paquete Java)

El grupo por defecto es `ec.com.smx.base`. Reemplázalo por el grupo correcto según los [estándares de nomenclatura](../../project-naming-standards/SKILL.md).

| Archivo / Ubicación | Qué reemplazar |
|--------------------|---------------|
| `build.gradle` (raíz) | `group = 'ec.com.smx.base'` |
| `{modulo}/build.gradle` | `group = 'ec.com.smx.base'` |
| `ci/README.md` | referencias al paquete base |
| `ci/helm/values.yaml` | referencias al paquete base |
| Archivos `.java` en `client/` | paquete `ec.com.smx.base` |
| Archivos `.java` en `core/` | paquete `ec.com.smx.base` |
| Archivos `.java` en `services/` | paquete `ec.com.smx.base` |
| Archivos `.java` en `vo/` | paquete `ec.com.smx.base` |
| Carpetas físicas `ec/com/smx/base/` | Renombrar a `ec/com/smx/{sistema}/` |

---

## Keycloak — campo `resource`

Actualiza el campo `resource` (nombre del cliente Keycloak) en los perfiles de entorno:

| Archivo | Entorno |
|---------|---------|
| `application-CONSOLA.yaml` | Desarrollo local |
| `application-PRUEBAS.yaml` | Pruebas / QA |
| `application-PRODUCCION.yaml` | Producción |

---

## CI/CD

| Archivo | Qué personalizar |
|---------|-----------------|
| `Jenkinsfile` | Campo `namespace` (espacio de trabajo K8s) |
| `ci/helm/values.yaml` | Esquema de base de datos |
| `ci/docker/DockerfileCI` | Nombre del responsable del proyecto |
| `ci/helm/Chart.yaml` | Nombre del responsable del proyecto |

---

## Consejo: refactorizar con IntelliJ IDEA

Para reemplazar el prefijo o el grupo de forma masiva en todo el proyecto:

1. Selecciona el texto a reemplazar y abre **Refactor → Rename**.
2. Activa **"In Whole Project"**.
3. Marca **"Search for text occurrences"**.
4. Selecciona el scope **"All places"**.
5. Confirma y revisa los cambios antes de aplicar.
