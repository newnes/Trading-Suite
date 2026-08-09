![Harmonic Patterns SwingCore Pro](Harmonic-Patterns-SwingCore-Pro.png)

# Harmonic Patterns SwingCore.

Indicador de análisis técnico para la detección y visualización de patrones armónicos sobre el gráfico, con proyección de niveles de Fibonacci y sistema de alertas configurable.

---

## Contenido

- [Qué es este indicador](#qué-es-este-indicador)
- [Qué NO es este indicador](#qué-no-es-este-indicador)
- [El problema real](#el-problema-real-detectarla-estructura-no-medir-el-patrón)
- [El enfoque de este indicador](#el-enfoque-de-este-indicador)
- [Breve contexto histórico](#breve-contexto-histórico)
- [Estructura de patrones](#estructura-de-patrones)
- [Tabla de patrones y ratios](#tabla-de-patrones-y-ratios)
- [Método de validación geométrica](#método-de-validación-geométrica-solo-pro)
- [Características](#características)
- [Características técnicas](#características-técnicas)
- [Versiones](#versiones)
- [Parámetros principales](#parámetros-principales)
- [Sistema de alertas](#sistema-de-alertas-5-canales)
- [Aviso de responsabilidad](#aviso-de-responsabilidad)
- [Contacto](#contacto)

---

## Qué es este indicador

Es una **herramienta de análisis visual**. Su función es identificar en el gráfico estructuras que cumplen las relaciones geométricas de seis patrones armónicos clásicos —Gartley, Bat, Butterfly, Crab, Cypher y Shark— en sus variantes alcista y bajista, y representarlas de forma clara junto con sus niveles de proyección.

El indicador dibuja los segmentos del patrón, etiqueta el punto de finalización, proyecta niveles de retroceso y extensión de Fibonacci a partir del patrón más reciente, y puede emitir una alerta cuando se detecta uno nuevo.

---

## Qué "NO" es este indicador

- **No es un sistema de trading automático.** No abre, cierra ni gestiona operaciones.
- **No genera señales de compra o venta.** Muestra estructuras geométricas; la interpretación y cualquier decisión corresponden por completo al usuario.
- **No predice el precio.** Los niveles de Fibonacci son referencias de proyección geométrica, no pronósticos.
- **No garantiza que un patrón detectado se resuelva de ninguna manera concreta.** Un patrón armónico es una figura de análisis técnico, y su aparición no implica un resultado.

---

## El problema real: detectar la estructura, no medir el patrón

Conviene ser transparente sobre dónde reside la dificultad técnica de este tipo de indicadores.

Medir un patrón armónico —comprobar si las proporciones entre sus segmentos se acercan a los ratios de Fibonacci— es, en el fondo, aritmética directa. Esa **no** es la parte difícil.

La parte difícil, y donde la mayoría de los detectores fallan, es el paso previo: **identificar qué es un pico y qué es un valle verdaderamente relevante en tiempo real**, especialmente en marcos temporales bajos como M1, donde el ruido de precio es considerable.

Aquí no existe una respuesta única y objetiva. La detección de máximos y mínimos significativos depende de varios parámetros (sensibilidad, ventana de observación, prominencia mínima, separación entre extremos) y puede abordarse con distintos modelos matemáticos, cada uno con sus propias concesiones:

- Si el detector es **demasiado sensible**, marca ruido como si fueran giros reales y produce patrones espurios.
- Si es **demasiado grueso**, pasa por alto estructuras válidas.

La pregunta central —*cuánto suavizado es adecuado y cuánto es excesivo*— no tiene una solución universalmente correcta. Es un problema intrínsecamente subjetivo, y cualquier detector honesto es, en realidad, una toma de posición sobre ese equilibrio.

---

## El enfoque de este indicador

Este indicador aborda esa dificultad con un método **empírico y alternativo** de identificación de la estructura de precio: empírico porque su configuración se deriva de la observación sobre datos reales, y alternativo porque es uno de los varios caminos posibles para resolver un problema que, como se explicó, no admite una única solución.

Construirlo implicó integrar varias disciplinas:

- **Procesamiento de señal**, para tratar la serie de precio antes de buscar extremos y reducir el impacto del ruido.
- **Geometría analítica**, ya que cada patrón es un conjunto de relaciones espaciales entre cinco puntos.
- **Proporciones y relaciones métricas** (los ratios de Fibonacci) como criterio de validación entre segmentos.
- **Lógica de validación combinatoria**: alternancia estricta de picos y valles, y comprobación de las desigualdades geométricas propias de cada patrón.

El resultado es un pipeline que primero resuelve la estructura de swings y solo después aplica la medición de patrones sobre esa estructura ya depurada.

---

## Breve contexto histórico

Los patrones armónicos tienen una larga tradición en el análisis técnico. Su origen suele situarse en el trabajo de H. M. Gartley (1935), y fueron formalizados con proporciones de Fibonacci por autores posteriores, entre ellos Scott Carney, quien sistematizó varios de los patrones que hoy se consideran estándar (como Bat, Crab y Shark). La técnica, por tanto, tiene décadas de recorrido.

Lo que ha cambiado en los últimos años es el intento de automatizar esta lectura en marcos temporales bajos, donde —como se ha descrito— la detección fiable de la estructura de precio se convierte en el verdadero cuello de botella.

---

## Estructura de patrones

Todos los patrones se identifican sobre una secuencia de cinco puntos de giro, alternando picos y valles.

**Patrón alcista** (X = valle):
X → A → B → C → D
V P V P V



**Patrón bajista** (X = pico):
X → A → B → C → D
P V P V P



Donde **P** = pico y **V** = valle.

> **Nota sobre Shark:** este patrón utiliza la notación **X‑A‑B‑C‑D**, a diferencia de la notación **O‑X‑A‑B‑C** empleada en otras implementaciones de referencia. Tenlo en cuenta al comparar la lectura de Shark con la de otros patrones o con otras herramientas.

---

## Tabla de patrones y ratios

| Patrón | AB/XA | XD/XA | Característica |
|---|---|---|---|
| **Gartley** | 61.8% | 78.6% | Clásico, retroceso moderado |
| **Bat** | 38.2–50% | 88.6% | Retroceso profundo en D |
| **Butterfly** | 78.6% | 127.2–161.8% | Extensión extrema |
| **Crab** | 38.2–61.8% | 161.8% | Extensión máxima |
| **Cypher** | BC/XA: 1.13–1.414 | CD/XC: 78.6% | C rebasa a A |
| **Shark** | XD/XA: 88.6% | CD/BC: 1.13–1.618 | D ≤ X (alcista) / D ≥ X (bajista) |

---

## Método de validación geométrica (SOLO PRO)

Además del método clásico basado en ratios de Fibonacci, la versión PRO incluye un **motor de validación geométrica** que verifica la estructura de precios de cada patrón.

### ¿Qué hace?

En lugar de basarse únicamente en proporciones numéricas, el método geométrico valida que los puntos X-A-B-C-D cumplan **relaciones de orden estrictas** entre sí. Esto significa que no solo se verifican los ratios, sino también la **estructura espacial** del patrón.

### Ejemplo: Gartley Alcista
Condiciones geométricas:

X < A (X es valle, A es pico)

A > B (A es más alto que B)

B > X (B es más alto que X)

C > B (C es más alto que B)

C < A (C es más bajo que A)

D < C (D es más bajo que C)

D ≤ B (D es igual o más bajo que B)

D > X (D es más alto que X)

text

Si alguna condición falla, el patrón **no se valida**, incluso si los ratios de Fibonacci coinciden.

### Ventajas del método geométrico

| Ventaja | Descripción |
|---------|-------------|
| **Mayor precisión** | Verifica la estructura real del precio, no solo ratios |
| **Menos falsos positivos** | Filtra patrones que cumplen ratios pero tienen estructura incorrecta |
| **Más robusto** | Menos sensible a la tolerancia de ratios |
| **Detección más temprana** | Puede identificar patrones en formación |

### Comparativa: Clásico vs Geométrico

| Aspecto | Método Clásico | Método Geométrico |
|---------|---------------|-------------------|
| **Base** | Ratios Fibonacci | Estructura de precios |
| **Validación** | Proporciones numéricas | Relaciones de orden |
| **Tolerancia** | Parámetro ajustable | Condiciones exactas |
| **Falsos positivos** | Mayor | Menor |
| **Velocidad** | Más rápido | Similar |
| **Disponibilidad** | LITE y PRO | **SOLO PRO** |

---

## Características

- Detección de 6 patrones armónicos (Gartley, Bat, Butterfly, Crab, Cypher, Shark), alcistas y bajistas.
- Trazado de los segmentos del patrón y etiqueta en el punto de finalización.
- Proyección de niveles de Fibonacci (retrocesos y extensiones) del patrón más reciente.
- **Dos métodos de validación seleccionables:**
  - **Clásico:** basado en ratios de Fibonacci (**disponible en LITE y PRO**)
  - **Geométrico:** basado en estructura de precios (**SOLO PRO**)
- Sistema de alertas configurable, con número de repeticiones ajustable.
- Visualización de la estructura de swings sobre el gráfico.

---

## Características técnicas

- **Base de datos:** velas Heiken Ashi (suavizado de precio).
- **Filtro:** Savitzky-Golay 7/3 para el procesamiento de la señal antes de buscar extremos.
- **Detección de estructura:** prominencia mínima + distancia mínima entre extremos + alternancia forzada de picos y valles.
- **Validación:** ratios clásicos o reglas geométricas, según el método seleccionado.
- **Sistema de identificación:** firma basada en tiempo (datetime) que evita el repintado del patrón detectado.
- **Alertas:** hasta 5 canales configurables, con control de repeticiones para evitar spam.
- **Proyección Fibonacci:** hasta 7 niveles, en ambas direcciones (retroceso y extensión).

---

## Versiones

### LITE (gratuita)
- 1 patrón a la vez (bloqueado por sesión).
- Método clásico (ratios).
- Alertas básicas (visual + sonido).
- Ideal para pruebas y aprendizaje.

### PRO (de pago)
- **6 patrones simultáneamente.**
- **Motor geométrico** (validación por estructura de precio).
- **Alertas multicanal** (5 canales: visual, sonido, push, email, log).
- Análisis multi-timeframe.
- Historial de patrones detectados.
- Exportación a CSV.
- Soporte premium.

### Comparativa LITE vs PRO

| Característica | LITE | PRO |
|----------------|------|-----|
| Patrones simultáneos | 1 a la vez | **6 simultáneos** |
| Método clásico (ratios) | ✅ | ✅ |
| **Método geométrico** | ❌ | **✅** |
| Validación por estructura | ❌ | **✅** |
| Alertas (canales) | 2 | **5** |
| Multi-timeframe | ❌ | **✅** |
| Historial de patrones | ❌ | **✅** |
| Exportación CSV | ❌ | **✅** |
| Soporte premium | ❌ | **✅** |
| Precio | **GRATIS** | **$97** |

---

## Parámetros principales

### Generales
- Activación de la detección y método de validación.
- Tolerancia de ratios (0.15 por defecto).
- Ventana de escaneo (1440 barras).

### Estructura
- Prominencia mínima (2.0).
- Separación entre extremos (80 barras).
- Distancia mínima (40 barras).

### Visualización
- Mostrar/ocultar porcentajes.
- Líneas horizontales desde D.
- Niveles de Fibonacci.

### Alertas
- Activación.
- Número de repeticiones (5 por defecto).

---

## Sistema de alertas (5 canales)

| Canal | Descripción | Configuración |
|---|---|---|
| **1. Visual** | Pop-up en el terminal MT5 | `Alert_Visual = true` |
| **2. Sonido** | Reproducción de archivo WAV | `Alert_Sonido = true` |
| **3. Push** | Notificación en el móvil | `Alert_Notificacion = true` |
| **4. Email** | Informe detallado por correo | `Alert_Email = true` |
| **5. Log** | Registro en la pestaña Expertos | `Alert_Log = true` |

---

## Aviso de responsabilidad

Este indicador se ofrece **exclusivamente con fines informativos y demostrativos**, como herramienta de apoyo al análisis técnico.

No constituye asesoría financiera, de inversión ni recomendación de operación alguna. La detección de patrones es el resultado de un cálculo geométrico y no representa una predicción del comportamiento futuro del mercado.

El rendimiento pasado no garantiza resultados futuros. La operación en mercados financieros conlleva un riesgo elevado de pérdida.

**Usted asume la totalidad del riesgo derivado de cualquier decisión que tome con base en este indicador.** El autor no se hace responsable de pérdidas, daños o perjuicios de ningún tipo resultantes de su uso.

---

## Contacto

| Contacto | Detalle |
|----------|---------|
| **Autor** | Nestor Mendez |
| **Email** | nestor.boza@gmail.com |
| **GitHub** | https://github.com/newnes |

---

*Versión: 1.0 | Última actualización: Agosto 2026 | Copyright © 2026, Nestor Mendez*
