---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'F-Strings - Parte 2/2' -->

# <!-- fit --> F-Strings
## Formateo moderno (Python 3.6+)
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Adoptar el estándar moderno de formateo de texto en Python.
- Gancho: "¿Y si les dijera que existe una forma más rápida, más corta y más fácil de leer que todo lo anterior?"
-->

---

<!-- _header: 'La solución moderna' -->

# F-Strings (Formatted String Literals)

**Sintaxis:**
```python
nombre = "Ana"
edad = 20

mensaje = f"Hola, me llamo {nombre} y tengo {edad} años"
print(mensaje)
```

**¡Más simple y legible!**

<!--
NOTAS DEL ORADOR:
- La "f" mágica antes de las comillas.
- Las variables van DIRECTAMENTE donde las querés.
- Es lo que todos esperaban que fuera programar.
-->

---

<!-- _header: 'Comparación directa' -->

# Antes vs Ahora

**Con .format():**
```python
mensaje = "{} tiene {} años".format(nombre, edad)
```

**Con f-string:**
```python
mensaje = f"{nombre} tiene {edad} años"
```

**Ventajas:**
* Más corto
* Variables en su lugar
* Más intuitivo

<!--
NOTAS DEL ORADOR:
- Menos ruido visual.
- Menos probabilidad de error (no hay que contar argumentos).
-->

---

<!-- _header: 'Expresiones dentro' -->

# Calcular en la misma línea

```python
a = 5
b = 3

print(f"La suma de {a} + {b} = {a + b}")
# La suma de 5 + 3 = 8

print(f"El doble de {a} es {a * 2}")
# El doble de 5 es 10

print(f"¿Es {a} mayor que {b}? {a > b}")
# ¿Es 5 mayor que 3? True
```

**Cualquier expresión Python**

<!--
NOTAS DEL ORADOR:
- Esto es poderoso: dentro de `{}` podés poner cualquier código Python válido (que devuelva un valor).
- Matemáticas, llamadas a funciones, accesos a listas...
-->

---

<!-- _header: 'Llamar funciones' -->

# Funciones en f-strings

```python
nombre = "ana garcía"

print(f"Nombre: {nombre.title()}")
# Nombre: Ana García

print(f"Mayúsculas: {nombre.upper()}")
# Mayúsculas: ANA GARCÍA

print(f"Longitud: {len(nombre)}")
# Longitud: 10
```

<!--
NOTAS DEL ORADOR:
- Evita tener que crear variables temporales solo para imprimir algo transformado.
-->

---

<!-- _header: 'Formateo de números' -->

# Decimales y precisión

**Limitar decimales:**
```python
pi = 3.14159265359

print(f"Pi: {pi:.2f}")    # Pi: 3.14
print(f"Pi: {pi:.4f}")    # Pi: 3.1416
```

**Separador de miles:**
```python
numero = 1234567

print(f"Número: {numero:,}")
# Número: 1,234,567
```

<!--
NOTAS DEL ORADOR:
- Hereda todo el poder del mini-lenguaje de formateo de `.format()`.
- La coma `,` como separador de miles es genial para números grandes.
-->

---

<!-- _header: 'Alineación' -->

# Alinear texto

```python
producto = "Pan"
precio = 50

# Izquierda (default)
print(f"|{producto:<15}|")  # |Pan            |

# Derecha
print(f"|{producto:>15}|")  # |            Pan|

# Centro
print(f"|{producto:^15}|")  # |      Pan      |

# Con precio
print(f"{producto:<15} ${precio:>6.2f}")
# Pan             $  50.00
```

<!--
NOTAS DEL ORADOR:
- Mnemotecnia para las flechas:
    - `<` apunta a la izquierda.
    - `>` apunta a la derecha.
    - `^` apunta arriba (centro).
-->

---

<!-- _header: 'Padding' -->

# Rellenar con caracteres

```python
numero = 42

# Rellenar con ceros
print(f"{numero:05}")     # 00042
print(f"{numero:08}")     # 00000042

# Rellenar con otros caracteres
print(f"{numero:*>10}")   # ********42
print(f"{numero:-^10}")   # ----42----
```

<!--
NOTAS DEL ORADOR:
- Útil para códigos postales, IDs, o decoración visual.
-->

---

<!-- _header: 'Debug con =' -->

# Python 3.8+: Self-documenting

```python
nombre = "Ana"
edad = 20
ciudad = "Buenos Aires"

# Antes
print(f"nombre: {nombre}")
print(f"edad: {edad}")
print(f"ciudad: {ciudad}")

# Con = (más rápido)
print(f"{nombre=}")    # nombre='Ana'
print(f"{edad=}")      # edad=20
print(f"{ciudad=}")    # ciudad='Buenos Aires'
```

**¡Perfecto para debugging!**

<!--
NOTAS DEL ORADOR:
- Truco secreto de expertos.
- Ahorra muchísimo tiempo al hacer "print debugging".
-->

---

<!-- _header: 'Multilinea' -->

# F-Strings en múltiples líneas

```python
nombre = "Ana García"
edad = 20
carrera = "Ingeniería en Computación"

reporte = f"""
Estudiante: {nombre}
Edad: {edad} años
Carrera: {carrera}
Estado: {'Activa' if edad < 100 else 'Inválido'}
"""

print(reporte)
```

**Usar triple comillas**

<!--
NOTAS DEL ORADOR:
- Ideal para generar emails, HTML, SQL, o reportes de texto.
-->

---

<!-- _header: 'Ejemplo práctico' -->

# Sistema de factura

```python
def generar_factura(producto, cantidad, precio):
    """Genera factura formateada."""
    subtotal = cantidad * precio
    iva = subtotal * 0.21
    total = subtotal + iva
    
    factura = f"""
    {'FACTURA':^40}
    {'-' * 40}
    Producto: {producto:<20} x{cantidad}
    Precio unitario: ${precio:>10.2f}
    Subtotal:        ${subtotal:>10.2f}
    IVA (21%):       ${iva:>10.2f}
    {'=' * 40}
    TOTAL:           ${total:>10.2f}
    """
    return factura

print(generar_factura("Notebook", 2, 50000))
```

<!--
NOTAS DEL ORADOR:
- Ejemplo integrador potente.
- Combina alineación, cálculos, formato numérico y multilínea.
-->

---

<!-- _header: 'Fechas y horas' -->

# Formatear datetime

```python
from datetime import datetime

ahora = datetime.now()

print(f"Fecha: {ahora:%d/%m/%Y}")
# Fecha: 30/01/2026

print(f"Hora: {ahora:%H:%M:%S}")
# Hora: 13:50:42

print(f"Completo: {ahora:%d/%m/%Y %H:%M}")
# Completo: 30/01/2026 13:50
```

<!--
NOTAS DEL ORADOR:
- Las f-strings soportan el protocolo de formateo de fechas directamente.
-->

---

<!-- _header: 'Diccionarios' -->

# F-Strings con dict

```python
usuario = {
    "nombre": "Ana",
    "edad": 20,
    "pais": "Argentina"
}

print(f"Usuario: {usuario['nombre']}")
print(f"Edad: {usuario['edad']}")
print(f"País: {usuario['pais']}")

# Resumen completo
print(f"{usuario['nombre']} ({usuario['edad']}) - {usuario['pais']}")
```

<!--
NOTAS DEL ORADOR:
- Ojo con las comillas: Si la f-string usa dobles `""`, las claves del dict deben usar simples `''` (o viceversa).
-->

---

<!-- _header: 'Ejercicio' -->

# Tarjeta de presentación

**Crea un programa que:**
1. Solicite nombre, edad y ciudad
2. Genere una tarjeta formateada con f-strings
3. Use alineación y decoración
4. Muestre el resultado

---

<!-- _header: 'Ejercicio - Solución' -->

# Posible solución

```python
nombre = input("Nombre: ")
edad = int(input("Edad: "))
ciudad = input("Ciudad: ")

tarjeta = f"""
{'=' * 40}
{nombre.upper():^40}
{'=' * 40}
Edad:     {edad} años
Ciudad:   {ciudad}
{'=' * 40}
"""

print(tarjeta)
```

---

<!-- _header: 'Resumen' -->

# Para recordar

**F-Strings:**
* Sintaxis: `f"texto {variable}"`
* Expresiones: `f"{a + b}"`
* Formateo: `f"{pi:.2f}"`
* Alineación: `f"{texto:>10}"`
* Debug: `f"{variable=}"`

**Ventajas:**
* Más legible
* Más rápido
* Más poderoso

**Usar siempre que sea posible**

<!--
NOTAS DEL ORADOR:
- Conclusión: Las f-strings son el presente y el futuro. Úsenlas.
-->

---

<!-- _class: centered -->

# ¡F-Strings completado!
## Formateo moderno dominado

---

<!-- _class: centered -->

# ¿Preguntas?
