---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Módulos - Parte 1/3' -->

# <!-- fit --> Módulos str
## Métodos de cadenas
Curso de Ingreso - Ingeniería en Computación

<!-- 
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Descubrir que los strings no son solo texto plano, sino objetos con superpoderes.
- Gancho: "¿Sabían que Python puede limpiar, buscar y transformar texto automáticamente sin que ustedes escriban algoritmos complejos?"
-->

---

<!-- _header: 'Los strings son objetos' -->

# Métodos de str

**Los strings tienen métodos incorporados:**
* Transformación: upper, lower, capitalize
* Búsqueda: find, index, count
* Validación: isdigit, isalpha, startswith
* Limpieza: strip, replace, split
* Y muchos más...

**No necesitás importar nada**

<!--
NOTAS DEL ORADOR:
- Aclarar que `str` es un tipo built-in, no un módulo que se importa.
- Pero funciona "como si fuera" un módulo lleno de herramientas para texto.
- Sintaxis de punto: `objeto.metodo()`.
-->

---

<!-- _header: 'Transformación' -->

# Cambiar mayúsculas/minúsculas

```python
texto = "Python es Genial"

print(texto.upper())      # "PYTHON ES GENIAL"
print(texto.lower())      # "python es genial"
print(texto.capitalize()) # "Python es genial"
print(texto.title())      # "Python Es Genial"
print(texto.swapcase())   # "pYTHON ES gENIAL"
```

**Útil para normalizar entradas**

<!--
NOTAS DEL ORADOR:
- Normalización: Para comparar "Hola" con "hola", pasamos ambos a `.lower()`.
- `title()` es genial para nombres propios.
-->

---

<!-- _header: 'Búsqueda' -->

# Encontrar subcadenas

```python
frase = "Python es un lenguaje Python"

# Buscar posición
print(frase.find("Python"))      # 0 (primera)
print(frase.find("Java"))        # -1 (no existe)
print(frase.rfind("Python"))     # 22 (última)

# Contar ocurrencias
print(frase.count("Python"))     # 2
print(frase.count("es"))         # 1
```

**find vs index:** find devuelve -1, index lanza error

<!--
NOTAS DEL ORADOR:
- `find` es "seguro" (no rompe el programa).
- `index` es estricto (rompe si no está). Usar `try-except` con `index`.
-->

---

<!-- _header: 'Verificación' -->

# Comprobar contenido

```python
# Verificar si empieza/termina
texto = "archivo.txt"
print(texto.startswith("archivo"))  # True
print(texto.endswith(".txt"))       # True

# Verificar si está en
print("arc" in texto)               # True
print("jpg" in texto)               # False
```

**Útil para validar extensiones**

<!--
NOTAS DEL ORADOR:
- `startswith` y `endswith` aceptan tuplas: `archivo.endswith((".jpg", ".png"))`.
- `in` es el operador de pertenencia más pythónico.
-->

---

<!-- _header: 'Validación de tipo' -->

# Métodos is...

```python
"123".isdigit()      # True
"abc".isalpha()      # True
"abc123".isalnum()   # True (alfanumérico)
"   ".isspace()      # True (solo espacios)
"Python".istitle()   # True (cada palabra capitalizada)
"PYTHON".isupper()   # True
"python".islower()   # True
```

**Perfecto para validar entrada de usuario**

<!--
NOTAS DEL ORADOR:
- Antes de convertir con `int()`, podemos chequear con `.isdigit()`.
-->

---

<!-- _header: 'Limpieza' -->

# Eliminar espacios

```python
texto = "   Python   "

print(texto.strip())   # "Python" (ambos lados)
print(texto.lstrip())  # "Python   " (izquierda)
print(texto.rstrip())  # "   Python" (derecha)

# Eliminar caracteres específicos
url = "https://ejemplo.com"
print(url.strip("https://"))  # "ejemplo.com"
```

**strip es tu aliado para limpiar input**

<!--
NOTAS DEL ORADOR:
- Los usuarios siempre meten espacios de más sin querer. `strip()` al rescate.
-->

---

<!-- _header: 'Reemplazo' -->

# Sustituir texto

```python
texto = "Python 2.7 es viejo"

# Reemplazar
nuevo = texto.replace("2.7", "3.12")
print(nuevo)  # "Python 3.12 es viejo"

# Reemplazar con límite
texto2 = "a-b-c-d"
print(texto2.replace("-", " ", 2))  # "a b c-d"
```

**replace no modifica el original**

<!--
NOTAS DEL ORADOR:
- Recordar: Strings son INMUTABLES.
- `.replace()` devuelve una COPIA nueva. El original no cambia.
-->

---

<!-- _header: 'Dividir' -->

# split: string → lista

```python
# Dividir por espacios (default)
frase = "Python es genial"
palabras = frase.split()
print(palabras)  # ["Python", "es", "genial"]

# Dividir por carácter
csv = "nombre,edad,ciudad"
datos = csv.split(",")
print(datos)  # ["nombre", "edad", "ciudad"]

# Dividir con límite
texto = "a:b:c:d"
print(texto.split(":", 2))  # ["a", "b", "c:d"]
```

<!--
NOTAS DEL ORADOR:
- Fundamental para procesar archivos CSV o logs.
- `split()` sin argumentos se come todos los espacios en blanco repetidos.
-->

---

<!-- _header: 'Unir' -->

# join: lista → string

```python
# Unir con espacio
palabras = ["Python", "es", "genial"]
frase = " ".join(palabras)
print(frase)  # "Python es genial"

# Unir con coma
datos = ["Ana", "25", "Bariloche"]
csv = ",".join(datos)
print(csv)  # "Ana,25,Bariloche"

# Unir líneas
lineas = ["Línea 1", "Línea 2"]
texto = "\n".join(lineas)
```

**join es el inverso de split**

<!--
NOTAS DEL ORADOR:
- Sintaxis contraintuitiva: `separador.join(lista)`.
- Se lee: "Usar este separador para unir esta lista".
-->

---

<!-- _header: 'Formateo' -->

# Alineación y relleno

```python
texto = "Python"

# Centrar
print(texto.center(20, "-"))  # "-------Python-------"

# Alinear izquierda/derecha
print(texto.ljust(10))        # "Python    "
print(texto.rjust(10, "*"))   # "****Python"

# Rellenar con ceros
numero = "42"
print(numero.zfill(5))        # "00042"
```

<!--
NOTAS DEL ORADOR:
- Útil para interfaces de línea de comandos (CLI) prolijas.
-->

---

<!-- _header: 'Caso práctico' -->

# Validar email simple

```python
def validar_email(email):
    """Valida formato básico de email."""
    # Limpiar espacios
    email = email.strip()
    
    # Verificar longitud mínima
    if len(email) < 5:
        return False
    
    # Debe tener @ y .
    if email.count("@") != 1:
        return False
    
    if "." not in email:
        return False
    
    # @ no al principio ni final
    if email.startswith("@") or email.endswith("@"):
        return False
    
    return True

print(validar_email("  user@example.com  "))  # True
print(validar_email("invalido"))              # False
```

<!--
NOTAS DEL ORADOR:
- Ejemplo integrador.
- Combina `strip`, `len`, `count`, `in`, `startswith`.
-->

---

<!-- _header: 'Caso práctico' -->

# Normalizar nombre

```python
def normalizar_nombre(nombre):
    """Normaliza nombre propio."""
    # Eliminar espacios
    nombre = nombre.strip()
    
    # Capitalizar cada palabra
    nombre = nombre.title()
    
    # Eliminar espacios múltiples
    palabras = nombre.split()
    nombre = " ".join(palabras)
    
    return nombre

print(normalizar_nombre("  jUAN  pEREZ  "))
# "Juan Perez"
```

<!--
NOTAS DEL ORADOR:
- Truco ninja: `split()` y luego `join()` elimina espacios dobles internos.
-->

---

<!-- _header: 'Encadenamiento' -->

# Combinar métodos

```python
# Encadenar transformaciones
texto = "  PYTHON es GENIAL  "
resultado = texto.strip().lower().capitalize()
print(resultado)  # "Python es genial"

# Procesar entrada de usuario
nombre = input("Nombre: ").strip().title()
email = input("Email: ").strip().lower()
```

**Los métodos se pueden encadenar**

<!--
NOTAS DEL ORADOR:
- Fluent interface.
- Se lee de izquierda a derecha.
-->

---

<!-- _header: 'Ejercicio' -->

# Contar palabras únicas

**Crea una función que:**
1. Reciba una frase
2. Convierta a minúsculas
3. Divida en palabras
4. Elimine duplicados
5. Devuelva cantidad de palabras únicas

---

<!-- _header: 'Ejercicio - Solución' -->

# Posible solución

```python
def contar_palabras_unicas(frase):
    """Cuenta palabras únicas en frase."""
    # Normalizar
    frase = frase.lower()
    
    # Dividir
    palabras = frase.split()
    
    # Eliminar duplicados con set
    unicas = set(palabras)
    
    return len(unicas)

frase = "Python es genial y Python es poderoso"
print(contar_palabras_unicas(frase))  # 5
# Palabras únicas: python, es, genial, y, poderoso
```

---

<!-- _header: 'Referencia rápida' -->

# Métodos más usados

**Transformación:**
* `upper()`, `lower()`, `capitalize()`, `title()`

**Búsqueda:**
* `find()`, `count()`, `startswith()`, `endswith()`

**Validación:**
* `isdigit()`, `isalpha()`, `isalnum()`

**Limpieza:**
* `strip()`, `replace()`, `split()`, `join()`

---

<!-- _header: 'Resumen' -->

# Para recordar

**Métodos str:**
* No modifican original (inmutables)
* Se pueden encadenar
* Devuelven nuevos strings

**Más usados:**
* strip, split, join
* upper, lower, title
* startswith, endswith
* replace, find

**Próximo:**
* Módulo random

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?