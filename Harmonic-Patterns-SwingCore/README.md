
Si alguna condición falla, el patrón **no se valida**, incluso si los ratios de Fibonacci coinciden.

### Comparativa: Clásico vs Geométrico

| Aspecto | Método Clásico | Método Geométrico |
|---------|---------------|-------------------|
| **Base** | Ratios Fibonacci | Relaciones de orden |
| **Validación** | Proporciones numéricas | Condiciones de orden |
| **Tolerancia** | Parámetro ajustable | Condiciones exactas |
| **Falsos positivos** | Puede validar estructuras incorrectas | Filtra estructuras incorrectas |
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
- **Filtro de señal:** Savitzky-Golay 7/3 para el procesamiento de la serie de precio antes de buscar extremos.
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
