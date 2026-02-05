---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---
<!-- header: 'Debugging Guiado'-->
<!-- footer: 'Tacticas - 3' -->
<!-- _class: lead -->

# <!-- fit --> Debugging Guiado
## Aprender a encontrar errores
Técnicas Avanzadas de IA

---


# El Problema

Cuando pedís que te **corrijan** el código:
* Perdés la oportunidad de **aprender**
* No desarrollás habilidad de debugging
* Dependencia de la IA

---

<!-- _class: inverse -->

# <!-- fit --> El debugging es una habilidad
# <!-- fit --> Solo se desarrolla practicándola

---

# ¿Cuándo usarlo?

* Código que no funciona
* Ya invertiste tiempo buscando el error
* Errores **lógicos** especialmente
  * (el código corre pero da mal)

---

# ¿Por qué funciona?

* Desarrolla lectura crítica de código
* Formular hipótesis sobre comportamiento
* Habilidades **transferibles**
* Aprendés el proceso, no solo la solución

---

<!-- _class: code -->

# Plantilla Principal

```text
Tengo este código que debería hacer 
[descripción] pero obtiene [resultado]:

[código con error]

No me corrijas el código. En su lugar:
1. Ayudame a identificar qué parte es 
   responsable del problema
2. Explicame qué está haciendo esa parte
3. Haceme preguntas para descubrir el error
```

---

<!-- _class: code -->

# Variante: Con Mensaje de Error

```text
Estoy debuggeando este código:
[código con error]

Error obtenido:
[mensaje de error]

Lo que ya intenté:
- [intento 1]
- [intento 2]

¿Qué otras estrategias de debugging puedo 
usar? Guiame sin darme la solución directa.
```

---

<!-- _class: inverse -->

# <!-- fit --> No pidas correcciones
## Pedí que te enseñen a encontrar el error

