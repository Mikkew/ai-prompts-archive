# Prompt: Análisis y Actualización de pom.xml para JDK 21

Actúa como un experto en ingeniería de software especializado en Java, Maven y migraciones de JDK.

Tu tarea es analizar el archivo `pom.xml` de un proyecto Maven que se va a migrar a JDK 21, y **generar una versión actualizada y acoplada** del mismo.

---

## Fase 1: Análisis

### 1.1 Listado de dependencias

Lista todas las dependencias presentes en el `pom.xml`, incluyendo las gestionadas en `<dependencyManagement>`.

| Grupo | Artefacto | Versión actual | Ámbito | Gestión |
|-------|-----------|----------------|--------|---------|
|       |           |                |        |         |

---

### 1.2 Dependencias desactualizadas

Para cada dependencia que tenga una versión más reciente estable compatible con JDK 21:

| Dependencia | Versión actual | Versión objetivo | Fuente | Riesgo | Justificación |
|-------------|----------------|------------------|--------|--------|---------------|
|             |                |                  |        |        |               |

**Niveles de riesgo:**
- **Bajo**: Actualización menor (patch), cambios retrocompatibles
- **Medio**: Actualización menor con cambios significativos o actualización mayor con buena retrocompatibilidad
- **Alto**: Actualización mayor con breaking changes, requiere cambios en código

---

### 1.3 Compatibilidad con JDK 21

Detecta dependencias que puedan presentar problemas con JDK 21:

| Dependencia | Versión actual | Problema detectado | Alternativa / Solución | Versión recomendada |
|-------------|----------------|--------------------|------------------------|---------------------|
|             |                |                    |                        |                     |

**Problemas comunes a verificar:**
- Uso de APIs internas eliminadas (ej. `com.sun.*`, `sun.*`)
- Dependencia de versiones específicas de Java (ej. `java.version` < 17)
- Bibliotecas obsoletas sin soporte para JDK 21
- Bytecode generado incompatible con versiones superiores

---

### 1.4 Análisis de plugins

Verifica la compatibilidad de los plugins Maven con JDK 21:

| Plugin | Versión actual | Versión mínima requerida | Versión objetivo | Observaciones |
|--------|----------------|--------------------------|------------------|---------------|
| maven-compiler-plugin | | 3.11.0 | 3.13.0 | Configurar `<release>21</release>` |
| maven-surefire-plugin | | 3.2.5 | 3.5.2 | |
| maven-failsafe-plugin | | 3.2.5 | 3.5.2 | |
| maven-war-plugin | | 3.4.0 | 3.4.0 | Si es aplicación web |
| maven-source-plugin | | 3.3.0 | 3.3.0 | |
| maven-javadoc-plugin | | 3.6.0 | 3.10.1 | |

---

### 1.5 Resumen ejecutivo

| Métrica | Cantidad |
|---------|---------|
| Total de dependencias | |
| Dependencias actualizables | |
| Dependencias con problemas de compatibilidad | |
| Plugins a actualizar | |

**Acciones recomendadas priorizadas:**

#### Críticas (requeridas antes de la migración)
- [ ] 

#### Deseables (mejoran estabilidad o rendimiento)
- [ ] 

#### Opcionales (actualizaciones menores)
- [ ] 

---

## Fase 2: Generación del pom.xml actualizado

A continuación, se genera el contenido completo del nuevo `pom.xml` aplicando:

1. **Actualización de versiones** de dependencias identificadas
2. **Actualización de plugins** para compatibilidad con JDK 21
3. **Actualización de propiedades** de compilación
4. **Sustitución de dependencias incompatibles** por alternativas recomendadas
5. **Preservación de estructura**, comentarios, perfiles y configuración existente

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>${grupo.original}</groupId>
    <artifactId>${artefacto.original}</artifactId>
    <version>${version.original}</version>
    <packaging>${packaging.original}</packaging>

    <properties>
        <!-- Propiedades actualizadas para JDK 21 -->
        <maven.compiler.release>21</maven.compiler.release>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        
        <!-- Propiedades originales preservadas -->
        ${propiedades.originales}
    </properties>

    <dependencyManagement>
        <dependencies>
            <!-- Dependencias gestionadas actualizadas -->
        </dependencies>
    </dependencyManagement>

    <dependencies>
        <!-- Dependencias actualizadas -->
    </dependencies>

    <build>
        <pluginManagement>
            <plugins>
                <!-- Plugin management actualizado -->
            </plugins>
        </pluginManagement>
        <plugins>
            <!-- Plugins actualizados para JDK 21 -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.13.0</version>
                <configuration>
                    <release>21</release>
                    <parameters>true</parameters>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.5.2</version>
                <configuration>
                    <argLine>--enable-preview</argLine>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-failsafe-plugin</artifactId>
                <version>3.5.2</version>
            </plugin>
            <!-- Otros plugins preservados y actualizados -->
        </plugins>
    </build>

    <!-- Perfiles preservados -->
    <profiles>
        ${perfiles.originales}
    </profiles>
</project>
```
## Fase 3: Resumen de cambios aplicados
Dependencias actualizadas
Artefacto	Versión anterior	Versión nueva	Riesgo
Plugins modificados
Plugin	Versión anterior	Versión nueva
maven-compiler-plugin		3.13.0
maven-surefire-plugin		3.5.2
maven-failsafe-plugin		3.5.2
Propiedades modificadas
Propiedad	Valor anterior	Valor nuevo
maven.compiler.release	(no existía)	21
maven.compiler.source	(eliminada si existe)	-
maven.compiler.target	(eliminada si existe)	-
maven.compiler.release		21
Sustituciones realizadas
Dependencia original	Alternativa aplicada	Motivo



