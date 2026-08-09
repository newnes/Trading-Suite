![Harmonic Patterns SwingCore Pro](Harmonic-Patterns-SwingCore-Pro.png)

# Harmonic Patterns SwingCore

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
