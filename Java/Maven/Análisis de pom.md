# Prompt: Análisis de pom.xml para migración a JDK 21

Actúa como un experto en ingeniería de software especializado en Java, Maven y migraciones de JDK.

Tu tarea es analizar el archivo `pom.xml` de un proyecto Maven que se va a migrar a JDK 21. Debes:

## 1. Listado de dependencias
- Listar todas las dependencias (`groupId`, `artifactId`, versión actual) presentes en el `pom.xml`, incluyendo las gestionadas en `<dependencyManagement>` si existen.
- Presentar esta información en una tabla markdown.

## 2. Dependencias desactualizadas
Para cada dependencia que tenga una versión más reciente estable disponible:
- Versión actual
- Última versión estable compatible con JDK 21
- Fuente de la sugerencia (Maven Central, release notes, etc.)
- Nivel de riesgo de actualización (`bajo`, `medio`, `alto`) con una breve justificación

Presentar en tabla markdown.

## 3. Compatibilidad con JDK 21
- Detectar dependencias que **no sean compatibles con JDK 21** (uso de APIs internas eliminadas, require Java version específica, obsoletas, etc.)
- Para cada una, indicar:
  - Dependencia y versión actual
  - Problema detectado
  - Alternativa compatible o versión mínima requerida

Presentar en tabla markdown.

## 4. Resumen ejecutivo
Generar un resumen con:
- Número total de dependencias
- Dependencias actualizables
- Dependencias con problemas de compatibilidad
- Acciones recomendadas priorizadas:
  - **Críticas** (deben resolverse antes de la migración)
  - **Deseables** (mejoran estabilidad o rendimiento)
  - **Opcionales** (actualizaciones menores o cosméticas)

## 5. Consideraciones adicionales
Si se proporciona, considera también:
- Perfiles Maven (`<profiles>`)
- Propiedades de versión (`<properties>`)
- Plugins que puedan afectar la compilación con JDK 21

Utiliza un tono técnico pero claro, y estructura toda la salida en formato markdown con tablas, listas y secciones bien definidas.