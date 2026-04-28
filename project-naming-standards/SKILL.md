# Skill: Estándares de Nomenclatura de Proyectos

## Descripción
Este skill valida y genera nombres de repositorios, artefactos, grupos y módulos siguiendo los estándares internos de la compañía.

## Cuándo usarlo
- Al crear un nuevo repositorio en Bitbucket.
- Al definir el `groupId` y `artifactId` de un proyecto Java/Gradle.
- Al revisar si un nombre existente cumple con las convenciones internas.

---

## Regla general
> **Todos los nombres van en inglés.**

---

## 1. Nomenclatura de repositorios

El nombre del repositorio sigue el patrón `{nombre-corto-sistema}-{módulo}-{sufijo}`, donde el sufijo indica el tipo de proyecto.

| Tipo de proyecto | Sufijo | Ejemplos |
|-----------------|--------|---------|
| Servicios (backend) | `-root` | `fwk-base-root`, `publix-root`, `adj-root` |
| Aplicación web (frontend) | `-web` | `cym-web`, `publix-web`, `adj-web` |
| Aplicación móvil Flutter | `-mobile` | `cym-mobile`, `publix-mobile`, `adj-mobile` |
| Tarea programada (CronJob K8s) | `-cronjob` | `fwk-base-cronjob`, `publix-cronjob`, `capp-send-notification-cronjob` |
| Versión Internet de proyecto existente | incluir `inet` | `tthh-notifications-inet-root`, `tthh-notifications-inet-services`, `max-fruver-inet-web` |

---

## 2. Código de grupo (paquete Java)

El código de grupo es el paquete raíz compartido por todos los módulos de un mismo sistema.

| Sistema | Grupo |
|---------|-------|
| B2B | `ec.com.smx.b2b` |
| MAX | `ec.com.smx.sic` |
| SISPE | `ec.com.smx.sic.sispe` |
| Corporativo V2 | `ec.com.smx.corpv2` |
| Corporativo V1 | `ec.com.smx.corporativo` |

---

## 3. Código de artefacto

El código del artefacto sigue el formato `{sistema}-{módulo}`, separando palabras con `-`.

### Reglas clave
- El módulo debe expresarse en **plural** siempre que sea posible (ej. `proveedores`, no `proveedor`).
- El sufijo final determina el rol del artefacto dentro del proyecto.

### Sufijos por tipo de artefacto

| Tipo | Sufijo | Ejemplos |
|------|--------|---------|
| Implementación principal (único proyecto) | `-core` | `sispe-core`, `max-core` |
| Cliente/contrato (único proyecto) | `-cliente` | `sispe-cliente`, `max-cliente` |
| Implementación por módulo (varios módulos) | `-{módulo}-core` | `max-administracion-core`, `max-proveedores-core` |
| Cliente por módulo (varios módulos) | `-{módulo}-cliente` | `max-administracion-cliente`, `max-proveedores-cliente` |
| Utilitario por tecnología | `-utilitario-{tech}` | `max-utilitario-jsf`, `framework-utilitario-struts` |
| Aplicación web (war/jar/dist) | `-web` | `corporativo-web`, `publix-web`, `adj-web` |
| Solo servicios web (war/jar) | `-services` | `fwk-base-services`, `publix-services` |
| Empaquetado EAR | `-web-ear` | `corporativo-web-ear`, `b2b-pronto-pago-ws-ear` |
| Módulo de QA | `-qa` | `b2b-web-qa`, `flux-movil-qa` |
| Value Objects | `-vo` | `sispe-cliente-vo`, `fwk-base-vo` |
| Tarea CronJob | `-task` | `fwk-migration-task`, `capp-send-notification-task` |

---

## 4. Ejemplos rápidos

Consulta la tabla completa de ejemplos en [`references/examples.md`](references/examples.md).

---

## Referencias cruzadas
- Para crear un proyecto backend ver: [`../springboot-project-setup/SKILL.md`](../springboot-project-setup/SKILL.md)
- Para crear un proyecto frontend ver: [`../angular-project-setup/SKILL.md`](../angular-project-setup/SKILL.md)
