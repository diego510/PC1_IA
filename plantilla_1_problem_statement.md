# Plantilla 1 — Problem Statement Canvas
## Framework PROMPT | Fase P — Problema de Negocio
### AD5018 Inteligencia Artificial para Negocios | UTEC

---

**Equipo:**
- Integrante 1: Valeria Champac
- Integrante 2: _______________________________________________
- Integrante 3: _______________________________________________

**Fecha de entrega:** _______________  
**Versión del canvas:** v4 — actualizada para PC1

---

## SECCIÓN 1 — Definición del problema

### 1.1 Usuario afectado

Personas con discapacidad auditiva (sordera total o parcial) que pasan tiempo solas en su hogar o se desplazan por espacios cotidianos sin una persona oyente cerca que pueda advertirles sobre sonidos relevantes de su entorno.

### 1.2 Problema específico

Estas personas pueden no percibir oportunamente sonidos críticos o relevantes del entorno, como una alarma, un detector de humo, el timbre de una puerta o la bocina de un vehículo. Esto puede retrasar su reacción frente a situaciones de riesgo y limitar su autonomía en actividades cotidianas.

### 1.3 Causa raíz

La causa raíz es que muchos eventos importantes del entorno se comunican principalmente mediante señales acústicas, mientras que el usuario tiene acceso limitado o nulo a ese canal sensorial. Como consecuencia, información relevante puede no ser percibida en el momento en que ocurre.

### 1.4 Consecuencia medible

Las personas con discapacidad auditiva pueden no identificar oportunamente sonidos críticos de su entorno, lo que incrementa el riesgo de no reaccionar a tiempo ante eventos relevantes y reduce su autonomía.

Para esta propuesta académica se trabajará con un **baseline provisional** que permitirá estructurar la PC1:

- **Identificación correcta sin apoyo del MVP: 40 %.**
- **Tiempo promedio de reacción: 6 segundos.**

Estos valores se consideran **estimaciones académicas provisionales**, no resultados de una prueba real. La validación posterior del MVP se realizará con una muestra pequeña y manejable para el curso:

- **5 usuarios**;
- **10 eventos por usuario**;
- **50 observaciones de prueba en total**.

Los indicadores principales serán:

1. porcentaje de eventos críticos identificados correctamente;
2. tiempo promedio de reacción frente a dichos eventos.

> **Aclaración:** las 260 muestras mencionadas en el proyecto corresponden a audios de entrenamiento del modelo, no a personas participantes.

### 1.5 Declaración del problema — formato obligatorio

Las personas con discapacidad auditiva que permanecen solas en el hogar o se desplazan por espacios cotidianos tienen dificultad para identificar oportunamente eventos del entorno comunicados principalmente mediante señales acústicas —como alarmas, detectores de humo, timbres o bocinas— debido a su acceso limitado o nulo al canal auditivo, lo que incrementa la posibilidad de no reaccionar oportunamente ante eventos relevantes y reduce su autonomía.

---

## SECCIÓN 2 — Filtro de validación IA

| Pregunta | SÍ/NO | Justificación |
|---|---|---|
| ¿Una hoja de cálculo o un formulario resuelve esto? | NO | El problema exige reconocer patrones acústicos capturados por un micrófono en tiempo real. |
| ¿El problema escala con el volumen de datos o usuarios? | SÍ | El desempeño del clasificador puede mejorar al incorporar más ejemplos y mayor diversidad de condiciones. |
| ¿Hay un patrón repetitivo que un humano reconoce pero tarda en procesar? | SÍ | Los sonidos objetivo presentan patrones acústicos diferenciables. |
| ¿El problema requiere generar contenido, responder preguntas o razonar en lenguaje natural? | SÍ, de forma acotada | El resultado del clasificador debe convertirse en una alerta clara y accesible. |
| ¿Necesitas tanto predecir como explicar, comunicar o actuar? | SÍ | El componente analítico clasifica el sonido y el generativo comunica el resultado al usuario. |

---

## SECCIÓN 3 — Los dos componentes del producto

### 3.1 Componente analítico

**Tarea:** Clasificación.

**Clases:**
- alarma
- detector_humo
- timbre
- bocina
- ruido_de_fondo

**Nivel:** **A3**

El modelo se entrenará en una primera versión, se evaluarán los errores, se recolectarán nuevos datos en las condiciones problemáticas y luego se reentrenará para comparar la mejora.

### 3.2 Componente generativo

**Nivel:** **G1**

La capa de lenguaje recibe:
- clase predicha;
- score de confianza;
- nivel de criticidad.

Con esa información genera una alerta breve y accesible, expresando incertidumbre cuando el score no supera el umbral definido.

### 3.3 Patrón de conexión

**Patrón 1 — Modelo → lenguaje**

```text
Audio → Clasificador → Clase + score → Criticidad/umbral → G1 → Alerta
```

### 3.4 Dónde va la ambición del equipo

- [X] **Profundidad en A3 y piso en G1**

La prioridad es mejorar la confiabilidad de la detección. Un falso negativo en una alarma o detector de humo es más importante que una alerta redactada con poca sofisticación.

### 3.5 Métricas principales

- recall por clase;
- precision por clase;
- accuracy global;
- matriz de confusión;
- porcentaje de eventos identificados correctamente;
- tiempo de reacción.

### 3.6 Solo si el equipo solicita excepción

No aplica. El equipo sí entrenará un modelo de clasificación de audio.

---

## SECCIÓN 4 — Autoevaluación

| Pregunta | Respuesta |
|---|---|
| ¿El problema está descrito sin mencionar tecnología? | SÍ |
| ¿La consecuencia tiene indicadores medibles? | SÍ |
| ¿Los dos componentes están definidos? | SÍ |
| ¿El patrón de conexión está elegido? | SÍ |
| ¿Está clara la ambición del equipo? | SÍ |
| ¿Está diferenciada la cantidad de audios frente a la cantidad de usuarios? | SÍ |
| ¿Todos los integrantes pueden explicar el canvas? | *(completar en equipo)* |

---

*Framework PROMPT v2.0 — AD5018 UTEC | Plantilla 1 de 4*
