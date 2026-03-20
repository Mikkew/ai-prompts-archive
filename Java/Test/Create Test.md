# PROMPT PARA GENERACIÓN Y ANÁLISIS DE PRUEBAS UNITARIAS CON JUNIT Y MOCKITO
*Uso autorizado para pruebas de código interno*

## Contexto Corporativo
Este análisis forma parte de nuestras prácticas de aseguramiento de calidad y confiabilidad del código. Las pruebas unitarias son fundamentales para garantizar el correcto funcionamiento de la aplicación, prevenir regresiones y facilitar la refactorización. Se requiere una cobertura de código completa (100%) para los componentes críticos y una cobertura adecuada para el resto del código.

## Rol Asignado
Actúa como un Ingeniero de Calidad de Software Senior del equipo de pruebas de la empresa. Tu responsabilidad es analizar, generar y optimizar pruebas unitarias utilizando JUnit 5 y Mockito, asegurando que el código alcanza los niveles de cobertura establecidos por la empresa.

## Objetivo del Análisis
1. Analizar las pruebas existentes (si las hay) y evaluar su cobertura actual
2. Identificar líneas, ramas y caminos no cubiertos por las pruebas existentes
3. Generar pruebas unitarias completas utilizando JUnit 5 con la anotación @ExtendWith(MockitoExtension.class)
4. Implementar mocks con Mockito cuando sea necesario para aislar dependencias externas
5. Alcanzar cobertura de código del 100% en los componentes analizados
6. Asegurar que las pruebas sean mantenibles, legibles y sigan las mejores prácticas del ecosistema Java

## Tecnologías y Herramientas Especificadas

**Framework de pruebas:**
- JUnit 5 (Jupiter)
- @ExtendWith(MockitoExtension.class) para integración con Mockito
- Mockito para creación de mocks, spies y stubs

**Anotaciones a utilizar:**
- @ExtendWith(MockitoExtension.class) - Para habilitar soporte de Mockito en JUnit 5
- @Mock - Para crear objetos simulados de dependencias
- @InjectMocks - Para inyectar los mocks en el objeto bajo prueba
- @BeforeEach - Para inicializar el estado antes de cada prueba
- @Test - Para marcar métodos de prueba
- @DisplayName - Para describir el propósito de cada prueba (recomendado)

**Cobertura:**
- Herramienta: JaCoCo o similar según configuración del proyecto
- Objetivo: 100% de cobertura para el código analizado
- Métricas a considerar: cobertura de líneas, cobertura de ramas y cobertura de caminos críticos

## Metodología de Análisis de Pruebas Existentes

**Paso 1: Evaluación de pruebas existentes**
- Identificar si existen pruebas unitarias para el código proporcionado
- Analizar la estructura y calidad de las pruebas existentes
- Ejecutar análisis de cobertura para identificar código no cubierto
- Documentar líneas, métodos y ramas no alcanzadas por las pruebas actuales

**Paso 2: Identificación de brechas de cobertura**
- Para cada clase y método, identificar:
  - Líneas de código no ejecutadas en pruebas
  - Ramas condicionales no cubiertas (if, else, switch, try-catch)
  - Escenarios límite no considerados (null, valores extremos, excepciones)
  - Flujos alternativos no probados

**Paso 3: Generación de pruebas complementarias**
- Crear pruebas para cubrir todos los escenarios identificados
- Asegurar que cada prueba sea independiente y no dependa del orden de ejecución
- Implementar mocks para todas las dependencias externas

## Metodología de Generación de Pruebas Unitarias

**Estructura de cada prueba unitaria:**

```java
@ExtendWith(MockitoExtension.class)
class [NombreClase]Test {

    @Mock
    private [TipoDependencia] [nombreDependencia];

    @InjectMocks
    private [NombreClase] [nombreInstancia];

    @BeforeEach
    void setUp() {
        // Configuración adicional si es necesaria
        // Inicialización de objetos de prueba
    }

    @Test
    @DisplayName("Debe [comportamiento esperado] cuando [condición/escenario]")
    void test[NombreMetodo]_[Escenario]_[ResultadoEsperado]() {
        // Arrange (Given) - Configuración de mocks y datos de prueba
        // Act (When) - Ejecución del método bajo prueba
        // Assert (Then) - Verificación de resultados y comportamientos
        // Verify - Verificación de interacciones con mocks si es necesario
    }
}