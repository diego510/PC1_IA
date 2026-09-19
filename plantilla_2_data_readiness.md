# Plantilla 2 — Data Readiness Checklist
## Framework PROMPT | Fase R — Recursos de Datos
### AD5018 Inteligencia Artificial para Negocios | UTEC

---

**Equipo:**
- Integrante 1: Valeria Champac
- Integrante 2: _______________________________________________
- Integrante 3: _______________________________________________

**Fecha de entrega:** _______________

**Tipo de IA:** Clasificación de audio **A3** + capa de lenguaje **G1**.

---

## SECCIÓN 1 — Inventario de datos

### Parte A — Componente generativo

| # | Información | Formato | Estado |
|---|---|---|---|
| 1 | Clases del modelo | Tabla / JSON | SÍ |
| 2 | Criticidad por clase | Tabla / JSON | PARCIAL |
| 3 | Umbral por clase | Tabla | PARCIAL |
| 4 | Reglas de redacción | Prompt | PARCIAL |
| 5 | Aviso de privacidad | Texto | PARCIAL |
| 6 | Instrucciones de uso | Texto | PENDIENTE |

**Estrategia:** G1 con contexto fijo.

---

### Parte B — Componente analítico

#### Dataset objetivo inicial

| Clase | Muestras objetivo |
|---|---:|
| Alarma | 50 |
| Detector de humo | 50 |
| Timbre | 50 |
| Bocina | 50 |
| Ruido de fondo | 60 |
| **Total** | **260 muestras de audio** |

> **Importante:** 260 son **muestras de audio**, no participantes humanos.

Fuentes previstas:
- Freesound.org;
- Pixabay Audio;
- Zapsplat;
- grabaciones propias.

Formatos:
- `.wav`
- `.mp3`

**Variable objetivo:**

```text
categoria_de_sonido
```

Valores:
- alarma;
- detector_humo;
- timbre;
- bocina;
- ruido_de_fondo.

**Tipo de problema:** Clasificación multiclase.

---

### Parte C — Plan A3

1. entrenar V1;
2. medir recall, precision, accuracy y matriz de confusión;
3. identificar clases problemáticas;
4. recolectar 15–20 muestras adicionales por clase problemática;
5. reentrenar;
6. comparar V1 vs. V2.

---

### Parte D — Validación con personas

La validación del producto no requiere 260 personas.

Se propone:

- **5 usuarios**;
- **10 eventos por usuario**;
- **50 observaciones de prueba**.

En cada observación se registrará:

- tipo de evento;
- si fue identificado correctamente;
- tiempo de reacción;
- si la alerta fue comprensible;
- error o incidencia observada.

---

## SECCIÓN 2 — Semáforo de calidad

| Dimensión | Estado | Evidencia / comentario |
|---|---|---|
| Disponibilidad | 🟡 | Fuentes identificadas; falta completar colección final |
| Volumen | 🟡 | Meta: 260 audios |
| Calidad | 🟡 | Requiere revisión de clips |
| Relevancia | 🟢 | Las cinco clases coinciden con el problema |
| Legalidad | 🟡 | Falta registrar licencias por clip |
| Etiquetas | 🟢 | Clases conocidas |
| Balance | 🟡 | Debe verificarse al cerrar dataset |
| Diversidad | 🟡 | Debe incluir distintos niveles de ruido y contexto |
| Fuga / atajos | 🟡 | Evitar que una clase dependa de una sola fuente o volumen |
| Vigencia | 🟢 | Los sonidos no dependen de información temporal cambiante |
| Cobertura G1 | 🟢 | Se cubren las cinco clases |
| Permisos de agente | — | No aplica |

---

## SECCIÓN 3 — Bloqueantes

### Bloqueante 1 — Completar dataset

**Meta:** 260 muestras.

**Acción:** completar y organizar audios por clase.

**Responsable:** integrante de datos.  
**Fecha límite:** antes de PC1.

---

### Bloqueante 2 — Licencias

**Acción:** registrar fuente, enlace y licencia de cada clip externo.

**Responsable:** integrante de documentación.  
**Fecha límite:** antes de PC1.

---

### Bloqueante 3 — Umbrales

Umbrales iniciales propuestos:

| Clase | Criticidad | Umbral |
|---|---|---:|
| Detector de humo | Alta | 0.80 |
| Alarma | Alta | 0.80 |
| Bocina | Alta | 0.78 |
| Timbre | Media | 0.75 |
| Ruido de fondo | Baja | 0.70 |

Estos valores son de diseño inicial y se ajustarán después de evaluar V1.

---

## SECCIÓN 4 — Privacidad y legalidad

- Los audios de entrenamiento deben excluir voces identificables.
- El MVP no almacenará audio permanentemente.
- El usuario debe ser informado de que el micrófono está activo.
- Si se captan datos personales incidentalmente, se aplicará minimización y no almacenamiento.
- La Ley N.° 29733 puede ser relevante en el uso real del MVP.

---

## SECCIÓN 5 — Datos para evaluación

### Baseline académico provisional

- Identificación correcta sin MVP: **40 %**
- Tiempo promedio de reacción: **6 segundos**

### Validación propuesta

- 5 usuarios;
- 10 eventos por usuario;
- 50 observaciones.

### Meta de negocio

- ≥ 80 % de eventos críticos identificados;
- ≤ 3 segundos de reacción promedio.

---

## SECCIÓN 6 — Autoevaluación

| Pregunta | Respuesta |
|---|---|
| ¿Las fuentes están identificadas? | SÍ |
| ¿Está definido el volumen objetivo? | SÍ — 260 audios |
| ¿Está claro que 260 no son personas? | SÍ |
| ¿Existe plan de validación humana? | SÍ — 5 usuarios / 50 observaciones |
| ¿Existe estrategia A3? | SÍ |
| ¿Se identificaron riesgos de privacidad? | SÍ |
| ¿Falta completar la colección real? | SÍ |

---

*Framework PROMPT v2.0 — AD5018 UTEC | Plantilla 2 de 4*
