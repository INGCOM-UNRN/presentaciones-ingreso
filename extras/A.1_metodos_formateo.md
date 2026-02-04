---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'F-Strings - Parte 1/2' -->

# <!-- fit --> Formateo de Cadenas
## Métodos tradicionales
Curso de Ingreso - Ingeniería en Computación

<!-- 
NOTAS DEL ORADOR:
- Duración estimada: 2 minutos
- Objetivo: Conocer la historia del formateo de texto en Python para entender por qué las f-strings son geniales.
- Gancho: "¿Alguna vez intentaron pegar texto y números y les dio error? Vamos a ver cómo se solucionaba eso antes."
-->

---

<!-- _header: 'El problema' -->

# Combinar texto y variables

**Necesidad común:**
```python
nombre = "Ana"
edad = 20

# ¿Cómo mostrar esto bonito?
# "Hola, me llamo Ana y tengo 20 años"
```

**Varios métodos disponibles**

<!--
NOTAS DEL ORADOR:
- Es una tarea tan común que Python tiene 4 formas distintas de hacerlo (acumuladas en 30 años de historia).
- Vamos a ver las "viejas" primero.
-->

---

<!-- _header: 'Método 1' -->

# Concatenación con +

```python
nombre = "Ana"
edad = 20

mensaje = "Hola, me llamo " + nombre + \
          " y tengo " + str(edad) + " años"
print(mensaje)
```

**Problemas:**
* Difícil de leer
* Hay que convertir a string
* Muchos `+` y espacios

<!--
NOTAS DEL ORADOR:
- Este es el método "fuerza bruta".
- Propenso a errores: olvidarse espacios, olvidarse de convertir `str(edad)`.
- Muy lento de escribir.
-->

---

<!-- _header: 'Método 2' -->

# Operador % (estilo C)

```python
nombre = "Ana"
edad = 20

mensaje = "Hola, me llamo %s y tengo %d años" % (nombre, edad)
print(mensaje)
```

**Especificadores:**
* `%s` → string
* `%d` → entero
* `%f` → float

**Antiguo pero funciona**

<!--
NOTAS DEL ORADOR:
- Heredado del lenguaje C (printf).
- Es compacto, pero críptico si no sabés los códigos (%s, %d).
- Todavía se ve mucho en código viejo (Python 2) y en logs.
-->

---

<!-- _header: 'Método 3' -->

# Método .format()

```python
nombre = "Ana"
edad = 20

mensaje = "Hola, me llamo {} y tengo {} años".format(
    nombre,
    edad
)
print(mensaje)
```

**Con índices:**
```python
mensaje = "{0} tiene {1} años. {0} estudia Python".format(
    nombre,
    edad
)
```

<!--
NOTAS DEL ORADOR:
- Introducido en Python 3 (y backporteado a 2.7).
- Mucho más potente.
- Las llaves `{}` son marcadores de posición.
- Permite reordenar argumentos con índices `{0}`, `{1}`.
-->

---

<!-- _header: 'format() con nombres' -->

# Named placeholders

```python
mensaje = "Hola, me llamo {n} y tengo {e} años".format(
    n=nombre, 
    e=edad
)
print(mensaje)
```

**Más legible pero verboso**

<!--
NOTAS DEL ORADOR:
- Esto mejora la legibilidad de la cadena, pero hace la llamada a `.format()` muy larga.
-->

---

<!-- _header: 'Formateo de números' -->

# .format() avanzado

**Decimales:**
```python
precio = 19.99876
print("Precio: ${:.2f}".format(precio))
# Precio: $19.99
```

**Alineación:**
```python
print("|{:>10}|".format("derecha"))  # |   derecha|
print("|{:<10}|".format("izq"))      # |izq       |
print("|{:^10}|".format("centro"))   # |  centro  |
```

<!--
NOTAS DEL ORADOR:
- El "mini-lenguaje de formateo" de Python.
- `:>10` significa "Alinear a derecha, ancho 10".
- Esto es súper útil para tablas y reportes.
- ¡Lo bueno es que este mini-lenguaje se reutiliza en las f-strings! Así que apréndanlo bien.
-->

---

<!-- _header: 'Comparación' -->

# Métodos tradicionales

**Concatenación (+):**
* ❌ Difícil de leer
* ❌ Conversiones manuales

**Operador %:**
* ❌ Sintaxis arcaica
* ❌ Fácil confundirse

**Método .format():**
* ✅ Más legible
* ✅ Flexible
* ❌ Algo verboso

<!--
NOTAS DEL ORADOR:
- Resumen de la evolución hasta 2015.
-->

---

<!-- _header: 'Ejemplo práctico' -->

# Tabla con .format()

```python
productos = [
    ("Pan", 50),
    ("Leche", 100),
    ("Huevos", 75)
]

print("{:<10} {:>8}".format("Producto", "Precio"))
print("-" * 20)

for prod, precio in productos:
    print("{:<10} ${:>7.2f}".format(prod, precio))
```

**Salida:**
```
Producto     Precio
--------------------
Pan        $  50.00
Leche      $ 100.00
Huevos     $  75.00
```

<!--
NOTAS DEL ORADOR:
- Ejemplo real de alineación.
- Los precios alineados a la derecha son más fáciles de leer.
-->

---

<!-- _header: 'Limitaciones' -->

# ¿Por qué no usar siempre .format()?

**Ejemplo:**
```python
nombre = "Ana"
edad = 20
ciudad = "Buenos Aires"

# Muy largo y repetitivo
mensaje = "{} vive en {} y tiene {} años".format(
    nombre,
    ciudad,
    edad
)
```

**Necesitamos algo mejor...**

<!--
NOTAS DEL ORADOR:
- Problema: La separación entre la cadena y los valores (`.format(...)`) hace que haya que saltar con la vista de un lado a otro.
- Solución: F-Strings (próxima clase).
-->

---

<!-- _header: 'Resumen' -->

# Métodos tradicionales

**Concatenación (+):**
* Simple pero tedioso

**Operador %:**
* Estilo antiguo

**Método .format():**
* Poderoso pero verboso

**Próximo:**
* F-Strings (la solución moderna)

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?

```