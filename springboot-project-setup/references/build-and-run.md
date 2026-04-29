# Compilar y ejecutar un proyecto Spring Boot

## Requisitos

| Herramienta | Versión |
|------------|---------|
| Java | 21 |
| Gradle | 8.7 |

---

## Compilar el proyecto

### Windows
```cmd
gradlew clean build
```

### Linux / macOS
```bash
./gradlew clean build
```

> El artefacto compilado se genera en `{prefijo}-services/build/libs/`.

---

## Ejecutar la aplicación

### 1. Configurar el perfil activo

**Windows (variable de entorno permanente):**
```cmd
setx SPRING_PROFILES_ACTIVE "CONSOLA"
```

**Linux / macOS (variable de sesión):**
```bash
export SPRING_PROFILES_ACTIVE=CONSOLA
```

### 2. Navegar al directorio de artefactos
```bash
cd {prefijo}-services/build/libs/
```

### 3. Iniciar la aplicación
```bash
java -jar {prefijo}-services-1.0.0-SNAPSHOT.jar
```

---

## Verificar que la aplicación está en ejecución

```
GET http://localhost:8080/{contexto}/actuator/health
```

Respuesta esperada:
```json
{
  "status": "UP"
}
```

---

## Documentación de la API

| Recurso | URL |
|---------|-----|
| Actuator (salud y métricas) | `http://localhost:8080/{contexto}/actuator` |
| OpenAPI JSON | `http://localhost:8080/{contexto}/v3/api-docs` |
| Swagger UI | `http://localhost:8080/{contexto}/swagger-ui.html` |

---

## Obtener token OAuth2 / Keycloak

Para autenticar peticiones en entornos con Keycloak activo:

**Request:**
```http
POST /auth/realms/CFAVORITA-SSO-INTRANET/protocol/openid-connect/token
Content-Type: application/x-www-form-urlencoded

username={usuario}&password={contraseña}&grant_type=password&client_id={client_id}
```

**Uso del token en las peticiones:**
```http
Authorization: Bearer {access_token}
```

---

## Perfiles de entorno disponibles

| Perfil | Uso |
|--------|-----|
| `CONSOLA` | Desarrollo local |
| `PRUEBAS` | Entorno de QA |
| `PRODUCCION` | Entorno productivo |
