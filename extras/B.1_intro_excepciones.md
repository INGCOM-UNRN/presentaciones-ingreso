---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Excepciones - Parte 1/4' -->

# <!-- fit --> Excepciones
## Manejo de errores
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Entender que los errores son eventos esperables y manejables.
- Gancho: "¿Alguna vez un programa se les cerró de la nada y perdieron todo? Eso es una excepción no manejada."
-->

---

<!-- _header: 'Los errores existen' -->

# Los errores son parte del juego

**Todo programa puede fallar:**
* Usuario ingresa texto en lugar de número
* Archivo no existe
* División por cero
* Memoria llena
* Conexión de red perdida

**¿Cómo manejarlos profesionalmente?**

<!--
NOTAS DEL ORADOR:
- Principio de Murphy: Si algo puede salir mal, saldrá mal.
- El programador profesional ANTICIPA el error.
- Diferencia entre "Bug" (error de lógica) y "Excepción" (evento en tiempo de ejecución).
-->

---

<!-- _header: 'Programa frágil' -->

# Sin manejo de errores

```python
def dividir(a, b):
    return a / b

num1 = int(input("Numerador: "))
num2 = int(input("Denominador: "))

resultado = dividir(num1, num2)
print(f"Resultado: {resultado}")
```

**¿Qué pasa si el usuario ingresa "hola"?**
**¿O si ingresa 0 como denominador?**

<!--
NOTAS DEL ORADOR:
- Mostrar que el programa "explota" (Crash).
- La experiencia de usuario es terrible (mensajes en rojo crípticos).
-->

---

<!-- _header: 'Programa robusto' -->

# Con manejo de errores

```python
def dividir(a, b):
    if b == 0:
        raise ValueError("No se puede dividir por 0")
    return a / b

try:
    num1 = int(input("Numerador: "))
    num2 = int(input("Denominador: "))
    resultado = dividir(num1, num2)
    print(f"Resultado: {resultado}")
except ValueError as e:
    print(f"Error: {e}")
```

**El programa no se rompe**

<!--
NOTAS DEL ORADOR:
- "Graceful degradation" (Degradación elegante).
- El programa informa el problema y sigue o termina ordenadamente.
- Introducir `try` y `except` como conceptos de "intentar" y "capturar".
-->

---

<!-- _header: '¿Qué es una excepción?' -->

# Excepción

**Evento anormal que interrumpe el flujo:**
* Se "lanza" cuando hay error
* Si no se captura, el programa termina
* Si se captura, se puede manejar

**Analogía:**
* Alarma de incendio (excepción)
* Seguir el procedimiento (try-except)
* Evacuación segura (manejo correcto)

<!--
NOTAS DEL ORADOR:
- El flujo normal se corta. Se salta a la rutina de manejo de error.
-->

---

<!-- _header: 'Tipos comunes' -->

# Excepciones frecuentes

**ValueError:**
```python
int("abc")  # ValueError: no es un número
```

**TypeError:**
```python
"2" + 2  # TypeError: tipos incompatibles
```

**ZeroDivisionError:**
```python
10 / 0  # ZeroDivisionError
```

<!--
NOTAS DEL ORADOR:
- Familiarizarse con los nombres.
- Aprender a leer el Traceback para identificar el tipo.
-->

---

<!-- _header: 'Más tipos' -->

# Otras excepciones comunes

**IndexError:**
```python
lista = [1, 2, 3]
lista[10]  # IndexError: índice fuera de rango
```

**KeyError:**
```python
dict = {"a": 1}
dict["b"]  # KeyError: clave no existe
```

**FileNotFoundError:**
```python
open("noexiste.txt")  # FileNotFoundError
```

<!--
NOTAS DEL ORADOR:
- `IndexError` y `KeyError` son los reyes de las estructuras de datos.
-->

---

<!-- _header: 'Sin manejo' -->

# ¿Qué pasa sin try-except?

```python
numero = int("abc")  # Crash aquí
print("Esto nunca se ejecuta")
```

**Salida:**
```
Traceback (most recent call last):
  File "programa.py", line 1, in <module>
    numero = int("abc")
ValueError: invalid literal for int() with base 10: 'abc'
```

**Programa termina abruptamente**

<!--
NOTAS DEL ORADOR:
- Analizar la anatomía de un Traceback.
- Última línea: Tipo de error y mensaje.
- Líneas anteriores: Dónde ocurrió.
-->

---

<!-- _header: 'Con manejo' -->

# Con try-except

```python
try:
    numero = int("abc")
    print("Esto no se ejecuta")
except ValueError:
    print("Error: ingresá un número válido")

print("El programa continúa")
```

**Salida:**
```
Error: ingresá un número válido
El programa continúa
```

<!--
NOTAS DEL ORADOR:
- La magia es que "El programa continúa".
-->

---

<!-- _header: 'Filosofía' -->

# EAFP vs LBYL

**LBYL:** Look Before You Leap
```python
if b != 0:
    resultado = a / b
else:
    print("No se puede dividir por 0")
```

**EAFP:** Easier to Ask Forgiveness than Permission
```python
try:
    resultado = a / b
except ZeroDivisionError:
    print("No se puede dividir por 0")
```

**Python prefiere EAFP**

<!--
NOTAS DEL ORADOR:
- Concepto muy Pythonic.
- "Es más fácil pedir perdón que permiso".
- En Python, intentar y fallar es barato y limpio.
- LBYL (Mirar antes de saltar) puede tener "Race Conditions" (condiciones de carrera) en sistemas concurrentes.
-->

---

<!-- _header: 'Cuándo usar' -->

# ¿Cuándo manejar excepciones?

**✅ Usar try-except para:**
* Validar entrada de usuario
* Operaciones de archivo/red
* Conversiones de tipo
* Operaciones que pueden fallar

**❌ No usar para:**
* Control de flujo normal
* Validaciones simples (if)
* Ocultar bugs reales

<!--
NOTAS DEL ORADOR:
- No usar excepciones como `goto`.
- No capturar TODO (`except: pass`) porque ocultás errores legítimos.
-->

---

<!-- _header: 'Ejemplo práctico' -->

# Pedir número válido

```python
def pedir_numero(mensaje):
    """Pide número hasta que sea válido."""
    while True:
        try:
            valor = input(mensaje)
            return int(valor)
        except ValueError:
            print("❌ Debe ser un número entero")

# Usar
edad = pedir_numero("Edad: ")
print(f"Edad válida: {edad}")
```

<!--
NOTAS DEL ORADOR:
- Patrón de validación robusta con `while True` + `try-except`.
- Indestructible ante entradas del usuario.
-->

---

<!-- _header: 'Resumen' -->

# Para recordar

**Excepciones:**
* Eventos anormales
* Interrumpen el flujo
* Se pueden capturar

**Tipos comunes:**
* ValueError, TypeError
* ZeroDivisionError
* IndexError, KeyError

**Próximo:**
* try-except en detalle

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?
