---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'IA - Parte 4' -->

# <!-- fit --> Ejercicios con IA
## Práctica guiada de prompting
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Esta clase es 100% práctica.
- Necesitan tener acceso a al menos un LLM (ChatGPT, Claude, Gemini).
- El objetivo es que PRACTIQUEN, no que escuchen.
- Cada ejercicio tiene un objetivo de aprendizaje específico.
-->

---

<!-- _header: 'Objetivo' -->

# ¿Qué vamos a hacer?

**Practicar el uso de IA como herramienta de aprendizaje**

* Formular buenos prompts
* Comparar respuestas de diferentes LLMs
* Verificar y cuestionar las respuestas
* Aprender a iterar y mejorar

**Herramientas sugeridas:**
* ChatGPT (OpenAI)
* Claude (Anthropic)
* Gemini (Google)

<!--
NOTAS DEL ORADOR:
- Si solo tienen acceso a uno, está bien.
- ChatGPT tiene versión gratis (GPT-3.5).
- Claude tiene versión gratis limitada.
- Gemini de Google también es gratis.
- Lo importante es la PRÁCTICA, no la herramienta específica.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 1
## Comparar explicaciones

<!--
NOTAS DEL ORADOR:
- Objetivo: Entender que diferentes LLMs dan respuestas diferentes.
- Tiempo sugerido: 10-15 minutos.
- Si no tienen acceso a los 3, que comparen con un compañero.
-->

---

<!-- _header: 'Ejercicio 1' -->

# Mismo prompt, diferentes LLMs

**Prompt a usar:**
```
Soy estudiante de primer año de programación.
Explicame qué es una variable en Python.
Usá una analogía simple y un ejemplo de código.
```

**Tu tarea:**
1. Enviá este prompt a ChatGPT
2. Enviá el mismo prompt a Claude
3. Enviá el mismo prompt a Gemini

<!--
NOTAS DEL ORADOR:
- Noten que el prompt tiene CONTEXTO (estudiante primer año).
- Tiene OBJETIVO (explicar variable).
- Tiene FORMATO (analogía + código).
- Es un buen ejemplo de prompt estructurado.
-->

---

<!-- _header: 'Ejercicio 1' -->

# Analizá las respuestas

**Compará:**
* ¿Qué analogía usa cada uno?
* ¿Qué ejemplo de código dan?
* ¿Cuál te resultó más claro?
* ¿Alguno tiene errores?

**Pregunta reflexiva:**
¿Por qué las respuestas son diferentes si el prompt fue el mismo?

<!--
NOTAS DEL ORADOR:
- La respuesta: cada LLM tiene entrenamiento diferente.
- No hay "mejor" LLM universal, depende del contexto.
- A veces uno es mejor para código, otro para explicaciones.
- La lección: no confiar ciegamente en NINGUNO.
-->

---

<!-- _header: 'Ejercicio 1' -->

# Registro de respuestas

| Aspecto | ChatGPT | Claude | Gemini |
|:--------|:--------|:-------|:-------|
| Analogía usada | | | |
| Ejemplo de código | | | |
| Claridad (1-5) | | | |
| ¿Errores? | | | |

**Completá esta tabla con tus observaciones**

<!--
NOTAS DEL ORADOR:
- Dar 5 minutos para completar la tabla.
- Después pedir que compartan en voz alta.
- Discutir las diferencias encontradas.
- Preguntar: "¿Alguien encontró un error en alguna respuesta?"
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 2
## Mejorar un prompt malo

<!--
NOTAS DEL ORADOR:
- Objetivo: Experimentar la diferencia entre prompt malo y bueno.
- Tiempo sugerido: 10 minutos.
- Este ejercicio muestra el impacto del contexto y especificidad.
-->

---

<!-- _header: 'Ejercicio 2' -->

# Prompt inicial (malo)

**Enviá este prompt:**
```
explicame los loops
```

**Observá la respuesta:**
* ¿Es útil?
* ¿Es específica para Python?
* ¿Sabés qué nivel asume?

<!--
NOTAS DEL ORADOR:
- Este prompt es INTENCIONALMENTE malo.
- Sin contexto de nivel, sin lenguaje específico.
- Probablemente la respuesta sea genérica o demasiado avanzada.
- Algunos LLMs pueden asumir JavaScript u otro lenguaje.
-->

---

<!-- _header: 'Ejercicio 2' -->

# Mejorá el prompt

**Usá la estructura:**
❲CONTEXTO❳ + ❲OBJETIVO❳ + ❲RESTRICCIONES❳ + ❲FORMATO❳

**Ejemplo mejorado:**
```
[CONTEXTO] Soy principiante en Python (curso de ingreso).
[OBJETIVO] Explicame la diferencia entre while y for.
[FORMATO] Usá ejemplos simples con números del 1 al 5.
          Explicá paso a paso qué hace cada línea.
[RESTRICCIÓN] No uses conceptos avanzados.
```

<!--
NOTAS DEL ORADOR:
- Esta es LA FÓRMULA MÁGICA para buenos prompts.
- CONTEXTO: quién soy y qué sé (principiante, curso ingreso).
- OBJETIVO: qué quiero lograr (diferencia while/for).
- FORMATO: cómo quiero la respuesta (paso a paso, ejemplos).
- RESTRICCIONES: qué NO quiero (sin conceptos avanzados).
- Hacerles notar que cada parte tiene un propósito.
-->

---

<!-- _header: 'Ejercicio 2' -->

# Compará los resultados

**Antes (prompt malo):**
* Respuesta vaga/genérica
* Quizás mezcla lenguajes
* Nivel inadecuado

**Después (prompt mejorado):**
* Respuesta específica
* Ejemplos claros
* Nivel apropiado

**Conclusión:**
Mejor prompt → mejor respuesta

<!--
NOTAS DEL ORADOR:
- Dar tiempo para que comparen ambas respuestas.
- Preguntar: "¿Qué tan diferente fue la segunda respuesta?"
- Enfatizar: el esfuerzo de escribir un buen prompt VALE LA PENA.
- Es como preguntar bien a un humano: mejor pregunta, mejor respuesta.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 3
## Verificar código de IA

<!--
NOTAS DEL ORADOR:
- Objetivo: Aprender a NUNCA confiar ciegamente en código de IA.
- Tiempo sugerido: 15 minutos.
- Este ejercicio es CRÍTICO para desarrollar hábitos seguros.
-->

---

<!-- _header: 'Ejercicio 3' -->

# Pedí código a la IA

**Prompt:**
```
Escribí una función en Python que reciba
una lista de números y devuelva la suma
de los números pares. Explicá cada línea.
```

**Cuando recibas el código:**
1. Leé cada línea
2. ¿Entendés todo?
3. Copialo a Python y ejecutalo

<!--
NOTAS DEL ORADOR:
- Noten que pedimos EXPLICACIÓN de cada línea.
- Si la IA explica, es más fácil verificar.
- NUNCA copiar código sin leerlo primero.
- "Ejecutalo" es el test mínimo, pero no suficiente.
-->

---

<!-- _header: 'Ejercicio 3' -->

# Casos de prueba

**Probá con estos datos:**

```python
# Caso 1: Lista normal
suma_pares([1, 2, 3, 4, 5, 6])  # Esperado: 12

# Caso 2: Lista vacía
suma_pares([])  # Esperado: 0

# Caso 3: Solo impares
suma_pares([1, 3, 5, 7])  # Esperado: 0

# Caso 4: Números negativos
suma_pares([-2, -4, 3])  # Esperado: -6

# Caso 5: Un solo elemento
suma_pares([4])  # Esperado: 4
```

<!--
NOTAS DEL ORADOR:
- Los casos límite (vacía, solo impares, negativos) son CLAVE.
- Muchos códigos fallan en casos límite.
- Si algún test falla, hay que investigar por qué.
- Preguntar: "¿El código de la IA pasó TODOS los tests?"
-->

---

<!-- _header: 'Ejercicio 3' -->

# Checklist de verificación

**Marcá lo que verificaste:**

- [ ] ¿El código funciona con lista normal?
- [ ] ¿Maneja lista vacía sin error?
- [ ] ¿Funciona con números negativos?
- [ ] ¿Tiene nombre descriptivo?
- [ ] ¿Tiene docstring o comentarios?
- [ ] ¿Entendés cada línea?

**Si alguno falla:** Pedí a la IA que corrija

<!--
NOTAS DEL ORADOR:
- Esta checklist debería ser HÁBITO con cualquier código de IA.
- La última pregunta es la más importante: ¿ENTENDÉS cada línea?
- Si no entendés una línea, preguntá específicamente sobre ella.
- "¿Qué hace exactamente esta línea: [línea]?"
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 4
## Iterar con la IA

<!--
NOTAS DEL ORADOR:
- Objetivo: Aprender a tener una CONVERSACIÓN con la IA.
- Tiempo sugerido: 10 minutos.
- La iteración es más poderosa que un solo prompt perfecto.
-->

---

<!-- _header: 'Ejercicio 4' -->

# Conversación iterativa

**Prompt inicial:**
```
Explicame qué es una lista en Python.
```

**Después de la respuesta, seguí preguntando:**
```
¿Cómo agrego un elemento al final?
```

```
¿Y si quiero agregar varios elementos?
```

```
¿Cuál es la diferencia entre append y extend?
```

<!--
NOTAS DEL ORADOR:
- La IA RECUERDA el contexto de la conversación.
- Pueden profundizar sin repetir todo.
- Es como una clase particular infinita.
- Cada pregunta de seguimiento construye sobre la anterior.
-->

---

<!-- _header: 'Ejercicio 4' -->

# Profundizá con preguntas

**Preguntas de seguimiento útiles:**

* "¿Podés darme un ejemplo más simple?"
* "¿Qué pasa si hago X en vez de Y?"
* "¿Por qué usaste esa forma y no otra?"
* "¿Hay algún caso donde esto falle?"
* "¿Cómo verifico que entendí bien?"

**La IA recuerda el contexto de la conversación**

<!--
NOTAS DEL ORADOR:
- "¿Qué pasa si...?" es MUY poderosa para experimentar.
- "¿Por qué...?" te da el razonamiento detrás.
- "¿Hay algún caso donde falle?" revela limitaciones.
- La última es para auto-evaluación: "¿Cómo verifico que entendí?"
-->

---

<!-- _header: 'Ejercicio 4' -->

# Registrá tu aprendizaje

**Al final de la conversación:**

1. ¿Qué conceptos nuevos aprendiste?
2. ¿Qué ejemplos te resultaron útiles?
3. ¿Alguna respuesta te confundió?
4. ¿Pudiste aclarar las dudas?

**Tip:** Guardá las conversaciones útiles

<!--
NOTAS DEL ORADOR:
- Reflexionar después de aprender refuerza la memoria.
- Guardar conversaciones útiles sirve para repaso.
- Si algo confundió, anotarlo para preguntar al profe.
- Las conversaciones con IA pueden ser material de estudio.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 5
## Detectar errores de IA

<!--
NOTAS DEL ORADOR:
- Objetivo: Desarrollar el "olfato" para errores de IA.
- Tiempo sugerido: 10 minutos.
- La IA puede equivocarse, y lo hace con mucha confianza.
-->

---

<!-- _header: 'Ejercicio 5' -->

# Pedí algo que puede fallar

**Prompt (intencionalmente ambiguo):**
```
Dame código para ordenar una lista.
```

**Analizá la respuesta:**
* ¿Ordena ascendente o descendente?
* ¿Modifica la lista original o crea una nueva?
* ¿Funciona con cualquier tipo de dato?

<!--
NOTAS DEL ORADOR:
- El prompt es INTENCIONALMENTE ambiguo.
- La IA va a ASUMIR cosas que no dijimos.
- Esto ilustra por qué la especificidad importa.
- Preguntar: "¿Qué asumió la IA que ustedes no dijeron?"
-->

---

<!-- _header: 'Ejercicio 5' -->

# Identificá problemas comunes

**Cosas que la IA puede hacer mal:**

1. **Asumir cosas no dichas**
   * "Seguro quiere orden ascendente"

2. **Usar funciones que no existen**
   * `lista.ordenar()` ← No existe en Python

3. **Mezclar versiones**
   * Usar f-strings en ejemplo "compatible con Python 2"

4. **Dar código sin explicar**
   * Funciona pero no entendés por qué

<!--
NOTAS DEL ORADOR:
- Las "alucinaciones" son muy comunes.
- La IA inventa funciones con total confianza.
- SIEMPRE verificar que las funciones existan en la documentación.
- Si da código sin explicar, PEDIR explicación.
-->

---

<!-- _header: 'Ejercicio 5' -->

# Corregí y mejorá

**Si encontrás un error:**

```
Tu código tiene un problema: [descripción].
¿Podés corregirlo y explicar por qué
la versión anterior estaba mal?
```

**Esto te ayuda a:**
* Verificar que entendés el error
* Ver cómo la IA se autocorrige
* Aprender de los errores

<!--
NOTAS DEL ORADOR:
- Pedirle que EXPLIQUE el error es más valioso que solo la corrección.
- La IA puede autocorregirse, pero a veces se equivoca de nuevo.
- Si la explicación no tiene sentido, desconfiar.
- Aprender de los errores de la IA también es aprendizaje.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 6
## Crear tu propia explicación

<!--
NOTAS DEL ORADOR:
- Objetivo: Transformar conocimiento PASIVO en ACTIVO.
- Tiempo sugerido: 15 minutos.
- Este es el ejercicio más importante para el aprendizaje real.
- Basado en el Método de Feynman.
-->

---

<!-- _header: 'Ejercicio 6' -->

# De receptor a creador

**Paso 1:** Pedí a la IA que explique `if-elif-else`

**Paso 2:** Leé y entendé la explicación

**Paso 3:** Escribí TU PROPIA explicación
* Con tus palabras
* Con tus ejemplos
* Como si le explicaras a un compañero

<!--
NOTAS DEL ORADOR:
- El paso 3 es donde ocurre el aprendizaje real.
- NO es copiar, es RECREAR con sus propias palabras.
- Si no pueden explicarlo, no lo entienden de verdad.
- Dar tiempo para que escriban su explicación.
-->

---

<!-- _header: 'Ejercicio 6' -->

# Compará tu explicación

**Paso 4:** Pedí a la IA que evalúe tu explicación

```
Escribí esta explicación de if-elif-else para
un compañero principiante. ¿Es correcta?
¿Qué puedo mejorar?

[Pegá tu explicación aquí]
```

**Esto verifica que realmente entendiste**

<!--
NOTAS DEL ORADOR:
- La IA actúa como evaluador de su explicación.
- Si hay errores conceptuales, los va a señalar.
- También puede sugerir mejoras en claridad.
- Este feedback cierra el ciclo de aprendizaje.
-->

---

<!-- _header: 'Ejercicio 6' -->

# ¿Por qué este ejercicio?

**Objetivo:** Transformar conocimiento pasivo en activo

* **Pasivo:** Leer y entender explicación de IA
* **Activo:** Crear tu propia explicación

**Si podés explicarlo, lo entendés**

**Si no podés explicarlo, volvé a estudiar**

<!--
NOTAS DEL ORADOR:
- Este es el Método de Feynman en acción.
- Muchos creen que entienden porque "tiene sentido".
- Pero cuando intentan explicar, descubren huecos.
- Esta técnica es CLAVE para exámenes y entrevistas.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 7
## Explicación por Capas

<!--
NOTAS DEL ORADOR:
- Objetivo: Practicar la técnica de pedir explicaciones en múltiples niveles.
- Tiempo sugerido: 10 minutos.
- Esta técnica crea "puentes cognitivos" entre lo familiar y lo nuevo.
-->

---

<!-- _header: 'Ejercicio 7' -->

# Pedí explicación en 3 niveles

**Usá este prompt:**
```
Explicame qué es una función en Python en tres niveles:

1. Nivel 1: Como para alguien sin conocimientos 
   de programación (con analogía del mundo real)
2. Nivel 2: Con detalle técnico para estudiante 
   de primer año
3. Nivel 3: Con detalles de implementación 
   (parámetros, return, scope)
```

<!--
NOTAS DEL ORADOR:
- Los 3 niveles van de lo simple a lo complejo.
- Nivel 1: Analogía, sin jerga técnica.
- Nivel 2: Vocabulario técnico pero accesible.
- Nivel 3: Detalles de implementación.
-->

---

<!-- _header: 'Ejercicio 7' -->

# Analizá la respuesta

**Para cada nivel, preguntate:**

| Nivel | Pregunta clave |
|-------|----------------|
| 1 | ¿La analogía tiene sentido? |
| 2 | ¿Entiendo todos los términos? |
| 3 | ¿Puedo escribir código basándome en esto? |

**Si algún nivel no es claro:**
Pedí que lo reformule o dé otro ejemplo

<!--
NOTAS DEL ORADOR:
- Si no entienden el nivel 3, quizás necesitan más del nivel 2.
- Pueden pedir "Dame otra analogía" o "Explicá más el nivel 2".
- La idea es construir comprensión progresiva.
-->

---

<!-- _header: 'Ejercicio 7' -->

# ¿Por qué funciona esta técnica?

**Puentes cognitivos:**
* Conecta lo nuevo con lo conocido
* Múltiples perspectivas del mismo concepto
* Si no entienden en un nivel, quizás sí en otro

**Usalo cuando:**
* Un concepto es abstracto o difícil
* Querés verificar comprensión profunda
* Preparás una explicación para otros

<!--
NOTAS DEL ORADOR:
- El cerebro aprende conectando lo nuevo con lo conocido.
- Una analogía crea ese "gancho" mental.
- Si pueden explicar en los 3 niveles, realmente entienden.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 8
## Debugging Guiado

<!--
NOTAS DEL ORADOR:
- Objetivo: Aprender a debuggear CON ayuda pero SIN que la IA corrija.
- Tiempo sugerido: 15 minutos.
- El debugging es una habilidad CRÍTICA que solo se aprende practicando.
-->

---

<!-- _header: 'Ejercicio 8' -->

# Código con error intencional

**Copiá este código a Python:**
```python
def contar_vocales(texto):
    vocales = "aeiou"
    contador = 0
    for letra in texto:
        if letra in vocales:
            contador = contador + 1
    return contador

# Prueba
print(contar_vocales("HOLA MUNDO"))  # Esperado: 4
```

**Ejecutalo. ¿Da el resultado esperado?**

<!--
NOTAS DEL ORADOR:
- El código tiene un bug intencional (no detecta mayúsculas).
- NO decir cuál es el bug, que lo descubran.
- Dar tiempo para que ejecuten y vean que da 0.
-->

---

<!-- _header: 'Ejercicio 8' -->

# NO pidas que corrija

**Prompt INCORRECTO (no usar):**
```
Este código no funciona, corregilo.
```

**Prompt CORRECTO (usar este):**
```
Este código debería contar vocales pero 
devuelve 0 para "HOLA MUNDO" cuando esperaba 4.

No me corrijas el código directamente. En su lugar:
1. Ayudame a identificar qué parte puede fallar
2. Haceme preguntas para que descubra el error
3. Dame una pista sin revelar la solución
```

<!--
NOTAS DEL ORADOR:
- La diferencia es ENORME para el aprendizaje.
- El prompt correcto pide GUÍA, no SOLUCIÓN.
- Si piden corrección directa, no aprenden a debuggear.
- Este hábito es transferible a cualquier lenguaje.
-->

---

<!-- _header: 'Ejercicio 8' -->

# Seguí el diálogo

**Posible respuesta de la IA:**
> "¿Qué diferencia hay entre 'a' y 'A'? 
> ¿Tu string de vocales incluye ambas?"

**Tu trabajo:**
1. Pensá en la pista
2. Formulá tu hipótesis
3. Modificá el código
4. Probá de nuevo

**Repetí hasta que funcione**

<!--
NOTAS DEL ORADOR:
- La IA actúa como TUTOR, no como corrector automático.
- El estudiante tiene que PENSAR y proponer soluciones.
- Este proceso desarrolla el "olfato" para bugs.
- Preguntar: "¿Qué hipótesis tienen?"
-->

---

<!-- _header: 'Ejercicio 8' -->

# ¿Por qué no pedir corrección directa?

**Si la IA corrige:**
* Obtenés código que funciona
* Pero no desarrollás habilidad de debugging
* En el examen no hay IA que corrija

**Si la IA guía:**
* Desarrollás pensamiento crítico
* Aprendés a leer código
* La habilidad queda para siempre

**El debugging es como el músculo: sin ejercicio, no crece**

<!--
NOTAS DEL ORADOR:
- Volver a la metáfora del gimnasio.
- Si alguien hace las flexiones por vos, no desarrollás músculo.
- El debugging es el "músculo" más importante del programador.
- En entrevistas técnicas, te dan código roto y tenés que arreglarlo.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio 9
## Método de Feynman Inverso

<!--
NOTAS DEL ORADOR:
- Objetivo: Practicar enseñar a la IA para verificar comprensión.
- Tiempo sugerido: 15 minutos.
- "Si no podés explicarlo simple, no lo entendés" - Feynman.
-->

---

<!-- _header: 'Ejercicio 9' -->

# Enseñale a la IA

**Elegí un concepto que creas entender:**
* Variables
* Condicionales (if/else)
* Lazos (for/while)
* Listas

**Usá este prompt:**
```
Quiero explicarte qué es [concepto] como si 
fueras un estudiante que no sabe nada.

Tu rol es:
1. Escuchar mi explicación
2. Hacer preguntas si algo no queda claro
3. Señalar si uso términos sin definir
4. Pedirme ejemplos si soy muy abstracto

Empiezo: [tu explicación aquí]
```

<!--
NOTAS DEL ORADOR:
- La IA actúa como "estudiante molesto" que pregunta todo.
- Las preguntas revelan huecos en la comprensión.
- Si no pueden responder, hay que estudiar más.
-->

---

<!-- _header: 'Ejercicio 9' -->

# Ejemplo de interacción

**Vos explicás:**
> "Una variable es como una caja donde guardás cosas"

**La IA pregunta:**
> "¿Qué tipo de cosas puedo guardar? ¿Puedo guardar 
> más de una cosa? ¿Qué pasa si la caja ya tiene algo?"

**Ahora tenés que responder...**
¿Podés explicar sin quedarte trabado?

<!--
NOTAS DEL ORADOR:
- Las preguntas "obvias" de la IA son muy reveladoras.
- Si se quedan trabados, encontraron un hueco.
- Ese hueco es exactamente lo que necesitan estudiar.
- Dar tiempo para que intenten responder.
-->

---

<!-- _header: 'Ejercicio 9' -->

# ¿Por qué funciona?

**Enseñar es la forma más efectiva de aprender**

* Preguntas difíciles exponen conocimiento superficial
* La IA no se cansa ni te juzga
* Simula un estudiante infinitamente curioso
* Feedback inmediato sobre tu explicación

**Si podés explicarlo simple, lo entendés**
**Si no podés, ahí está tu próximo tema de estudio**

<!--
NOTAS DEL ORADOR:
- Richard Feynman usaba esta técnica.
- Es excelente para preparar exámenes.
- También sirve antes de explicar a un compañero.
- La IA como "compañero de estudio" es muy poderosa.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Ejercicio Integrador
## Resolver un problema completo

<!--
NOTAS DEL ORADOR:
- Objetivo: Aplicar TODO lo aprendido en un problema real.
- Tiempo sugerido: 20-30 minutos.
- Este ejercicio simula cómo deberían usar IA en la práctica.
-->

---

<!-- _header: 'Ejercicio integrador' -->

# El problema

**Crear un programa que:**
1. Pida al usuario N números
2. Calcule el promedio
3. Muestre cuántos están arriba del promedio
4. Muestre cuántos están abajo del promedio

**NO pidas el código completo a la IA**

<!--
NOTAS DEL ORADOR:
- El problema es lo suficientemente complejo para ser interesante.
- Pero no tan difícil que sea imposible sin IA.
- La clave: NO pedir el código completo.
- Usar IA para PARTES específicas, no para todo.
-->

---

<!-- _header: 'Ejercicio integrador' -->

# Usá la IA estratégicamente

**Preguntas permitidas:**
* "¿Cómo pido varios números al usuario?"
* "¿Cómo calculo el promedio de una lista?"
* "¿Cómo cuento elementos que cumplen condición?"

**NO permitido:**
* "Haceme el programa completo"
* "Resolvé este problema por mí"

<!--
NOTAS DEL ORADOR:
- Las preguntas permitidas son ESPECÍFICAS sobre técnicas.
- NO revelan el problema completo.
- Ustedes tienen que INTEGRAR las respuestas.
- Esa integración es donde ocurre el aprendizaje.
-->

---

<!-- _header: 'Ejercicio integrador' -->

# Proceso recomendado

1. **Diseñá el algoritmo** (pseudocódigo)
2. **Identificá qué no sabés**
3. **Preguntá puntualmente** a la IA
4. **Integrá las respuestas** en tu código
5. **Probá con casos** de prueba
6. **Verificá** que funciona

<!--
NOTAS DEL ORADOR:
- Este proceso es EL MODELO de cómo usar IA para aprender.
- El paso 1 (diseñar) es ANTES de consultar IA.
- El paso 2 (identificar dudas) requiere pensar primero.
- Los pasos 3-6 son el ciclo de consulta-integración-prueba.
-->

---

<!-- _header: 'Ejercicio integrador' -->

# Autoevaluación

**Al terminar, preguntate:**

- [ ] ¿Puedo explicar cada línea de mi código?
- [ ] ¿Usé la IA para aprender o para copiar?
- [ ] ¿Podría resolver algo similar sin IA?
- [ ] ¿Qué conceptos reforcé?
- [ ] ¿Qué me falta practicar más?

<!--
NOTAS DEL ORADOR:
- Estas preguntas son para auto-evaluación HONESTA.
- Si la mayoría es negativa, hay que cambiar el enfoque.
- La tercera pregunta es clave: "¿Podría sin IA?"
- Si la respuesta es no, todavía no aprendieron.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Resumen
## Buenas prácticas con IA

<!--
NOTAS DEL ORADOR:
- Momento de cerrar y consolidar lo aprendido.
- Pedir que compartan qué les sorprendió de la práctica.
- Preguntar qué ejercicio les resultó más útil.
-->

---

<!-- _header: 'Resumen' -->

# Lo que aprendimos

**Estructura de prompts:**
❲CONTEXTO❳ + ❲OBJETIVO❳ + ❲RESTRICCIONES❳ + ❲FORMATO❳

**Técnicas avanzadas:**
* Explicación por Capas (3 niveles)
* Debugging Guiado (pistas, no corrección)
* Feynman Inverso (enseñar para verificar)

**Verificación:**
* Siempre probar el código
* Cuestionar las respuestas

<!--
NOTAS DEL ORADOR:
- La estructura de prompts es la base de todo.
- Las 3 técnicas avanzadas son para aprendizaje profundo.
- Capas: entender desde múltiples perspectivas.
- Debugging: desarrollar el músculo de encontrar errores.
- Feynman: verificar que realmente entendés.
-->

---

<!-- _header: 'Resumen' -->

# Uso responsable

**La IA es herramienta, no muleta**

* **Usala para aprender**, no para copiar
* **Verificá siempre** las respuestas
* **Experimentá** con el código
* **Explicá** lo que aprendiste

**Si no podés explicarlo, no lo entendés**

<!--
NOTAS DEL ORADOR:
- Volver a la metáfora del gimnasio.
- La IA no puede hacer las flexiones mentales por ustedes.
- Si solo copian, no desarrollan músculo cognitivo.
- El examen va a ser sin IA - ahí se nota quién aprendió.
-->

---

<!-- _header: 'Próximos pasos' -->

# Seguí practicando

**En cada tema nuevo:**
1. Intentá primero sin IA (zona libre de IA)
2. Si te trabás, usá la estructura de prompt
3. Pedí explicación por capas si es abstracto
4. Debugging guiado si hay errores
5. Feynman inverso para verificar comprensión

**Recordá: la IA no puede hacer flexiones por vos**

<!--
NOTAS DEL ORADOR:
- El paso 1 es la "zona libre de IA" de Escamilla.
- Cada técnica tiene su momento de uso.
- Cerrar con la metáfora del gimnasio refuerza el mensaje.
- La práctica con estas técnicas construye habilidades REALES.
-->

---

<!-- _class: centered -->

# ¿Preguntas?

<!--
NOTAS DEL ORADOR:
- Momento para resolver dudas sobre los ejercicios.
- Preguntar: "¿Qué fue lo más difícil de la práctica?"
- Preguntar: "¿Qué van a hacer diferente ahora?"
- Recordar que pueden seguir practicando en casa.
-->
