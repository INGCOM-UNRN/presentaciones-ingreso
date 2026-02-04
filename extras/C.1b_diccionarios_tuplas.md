---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Estructuras de Datos - Parte 4/5' -->

# <!-- fit --> Diccionarios y Tuplas
## Mapeos e Inmutabilidad
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Dominar las dos estructuras de datos restantes fundamentales.
- Gancho: "¿Cómo guardan la agenda de contactos de su celular? ¿Una lista gigante? No, usan un sistema donde buscan 'Juan' y aparece su número. Eso es un diccionario."
-->

---

<!-- _header: 'Diccionarios (dict)' -->

# Clave y Valor

Un diccionario asocia una **clave** (única) con un **valor**.
Es como un diccionario real: buscás palabra (clave) → obtenés definición (valor).

```python
estudiante = {
    "nombre": "Ana",
    "edad": 20,
    "carrera": "Sistemas"
}

print(estudiante["nombre"])  # "Ana"
```

**Claves:** Deben ser inmutables (str, int, tuple).
**Valores:** Pueden ser cualquier cosa (listas, otros dicts).

<!--
NOTAS DEL ORADOR:
- Estructura de mapeo (Hash Map).
- Acceso casi instantáneo O(1), a diferencia de buscar en una lista O(n).
- Las claves son como las etiquetas de los buzones.
-->

---

<!-- _header: 'Acceso seguro' -->

# get() vs []

**Acceso directo (`[]`):**
```python
print(estudiante["nota"])  # ❌ KeyError si no existe
```

**Método `get()`:**
```python
print(estudiante.get("nota"))      # None (no falla)
print(estudiante.get("nota", 0))   # 0 (valor por defecto)
```

**Recomendación:** Usá `get()` si no estás seguro de que la clave exista.

<!--
NOTAS DEL ORADOR:
- El error `KeyError` es el equivalente a `IndexError` en listas.
- `get()` es el "airbag" de los diccionarios.
-->

---

<!-- _header: 'Modificación' -->

# Agregar y cambiar

Los diccionarios son **mutables**.

```python
datos = {"a": 1, "b": 2}

# Modificar existente
datos["a"] = 10

# Agregar nuevo
datos["c"] = 3

# Eliminar
del datos["b"]

print(datos)  # {"a": 10, "c": 3}
```

<!--
NOTAS DEL ORADOR:
- La sintaxis de agregar y modificar es la misma.
- Si la clave existe, la pisa. Si no, la crea.
-->

---

<!-- _header: 'Iteración' -->

# Recorrer un diccionario

```python
capitales = {"Argentina": "Buenos Aires", "Chile": "Santiago"}

# Solo claves (por defecto)
for pais in capitales:
    print(pais)

# Clave y Valor (items) - EL MÁS ÚTIL
for pais, ciudad in capitales.items():
    print(f"La capital de {pais} es {ciudad}")
```

**Métodos de vista:**
* `.keys()`: Claves
* `.values()`: Valores
* `.items()`: Pares (clave, valor)

<!--
NOTAS DEL ORADOR:
- `.items()` devuelve una tupla en cada vuelta, que desempaquetamos en `pais, ciudad`.
-->

---

<!-- _class: inverse -->

# <!-- fit --> Tuplas (tuple)
## Listas inmutables

<!--
NOTAS DEL ORADOR:
- Cambio de tema.
- Las tuplas son las hermanas serias y rígidas de las listas.
-->

---

<!-- _header: '¿Qué es una tupla?' -->

# Inmutabilidad

Una tupla es como una lista, pero **no se puede modificar** una vez creada.

**Sintaxis:** Paréntesis `()`
```python
punto = (10, 20)
colores = ("rojo", "verde", "azul")
```

**Intento de modificación fallará:**
```python
punto[0] = 5  # ❌ TypeError
```

<!--
NOTAS DEL ORADOR:
- ¿Por qué querríamos algo que no se puede cambiar?
- Seguridad (nadie me toca mis datos).
- Rendimiento (ligeramente más rápido).
- Hashable (pueden ser claves de diccionario).
-->

---

<!-- _header: 'Uso de tuplas' -->

# ¿Cuándo usarlas?

1.  **Datos constantes:** Días de la semana, coordenadas, configuraciones fijas.
2.  **Seguridad:** Garantizar que los datos no cambien accidentalmente.
3.  **Claves de diccionario:** Las listas no pueden ser claves, las tuplas sí.
4.  **Rendimiento:** Son ligeramente más rápidas que las listas.

<!--
NOTAS DEL ORADOR:
- Ejemplo: Coordenadas GPS (lat, lon). No tiene sentido agregarle una tercera dimensión de repente.
-->

---

<!-- _header: 'Unpacking' -->

# Desempaquetado

Asignar elementos de una tupla (o lista) a variables individuales.

```python
# Tupla de coordenadas
coordenadas = (10, 20, 30)

# Desempaquetado
x, y, z = coordenadas

print(f"x={x}, y={y}, z={z}")
```

**Intercambio de variables (swap):**
```python
a, b = 5, 10
a, b = b, a  # a=10, b=5
```

<!--
NOTAS DEL ORADOR:
- Una de las características más elegantes de Python.
- El swap en otros lenguajes requiere una variable temporal `temp`.
-->

---

<!-- _header: 'Tuplas y Funciones' -->

# Retorno múltiple

Las funciones pueden devolver múltiples valores usando tuplas implícitas.

```python
def min_max(numeros):
    return min(numeros), max(numeros)  # Retorna tupla

lista = [1, 5, 2, 8, 3]
menor, mayor = min_max(lista)

print(f"Mínimo: {menor}, Máximo: {mayor}")
```

<!--
NOTAS DEL ORADOR:
- En realidad la función devuelve UN solo objeto: una tupla.
- Pero nosotros lo vemos como múltiples valores.
-->

---

<!-- _header: 'Resumen' -->

# Diccionarios y Tuplas

**Diccionarios:**
* Pares Clave-Valor `{k: v}`.
* Acceso rápido por clave.
* Usar `get()` para evitar errores.
* Iterar con `.items()`.

**Tuplas:**
* Inmutables `()`.
* Útiles para datos fijos y retorno múltiple.
* Desempaquetado: `x, y = punto`.

**Próximo:**
* Módulos Random y Math.

<!--
NOTAS DEL ORADOR:
- Cierre.
-->