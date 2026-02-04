---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Excepciones - Parte 2/4' -->

# <!-- fit --> try-except
## Capturar y manejar errores
Curso de Ingreso - Ingeniería en Computación

<!-- 
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Dominar la sintaxis completa del manejo de errores.
- Gancho: "¿Cómo hacemos para que nuestro programa sobreviva a una división por cero? Le ponemos un paracaídas."
-->

---

<!-- _header: 'Estructura básica' -->

# try-except

**Sintaxis:**
```python
try:
    # Código que puede fallar
    codigo_peligroso()
except TipoExcepcion:
    # Qué hacer si falla
    manejar_error()
```

**Bloques:**
* `try` → intentar ejecutar
* `except` → capturar error

<!-- 
NOTAS DEL ORADOR:
- Analogía del trapecista (`try`) y la red de seguridad (`except`).
- Si el trapecista no cae, la red no se usa.
-->

---

<!-- _header: 'Ejemplo simple' -->

# Capturar ValueError

```python
try:
    edad = int(input("Edad: "))
    print(f"Tenés {edad} años")
except ValueError:
    print("Eso no es un número válido")
```

**Prueba:**
* Input "25" → Funciona
* Input "abc" → Captura error

<!-- 
NOTAS DEL ORADOR:
- Mostrar que el programa no se detiene si hay error, salta al `except`.
-->

---

<!-- _header: 'Capturar mensaje' -->

# Acceder al error (as)

```python
try:
    numero = int("abc")
except ValueError as error:
    print(f"Error capturado: {error}")
    print(f"Tipo: {type(error)}")
```

**Salida:**
```
Error capturado: invalid literal for int()...
Tipo: <class 'ValueError'>
```

<!-- 
NOTAS DEL ORADOR:
- `as e` o `as error` guarda la instancia de la excepción.
- Útil para logs o mensajes detallados.
-->

---

<!-- _header: 'Múltiples except' -->

# Capturar diferentes errores

```python
try:
    num1 = int(input("Numerador: "))
    num2 = int(input("Denominador: "))
    resultado = num1 / num2
    print(f"Resultado: {resultado}")
except ValueError:
    print("Error: Ingresá números válidos")
except ZeroDivisionError:
    print("Error: No se puede dividir por 0")
```

**Un except por tipo de error**

<!-- 
NOTAS DEL ORADOR:
- Manejo diferenciado. No es lo mismo equivocarse de número que dividir por cero.
- Permite dar feedback específico al usuario.
-->

---

<!-- _header: 'Capturar múltiples' -->

# Varios tipos en un except

```python
try:
    # Operación compleja
    resultado = operacion_compleja()
except (ValueError, TypeError, KeyError):
    print("Error en datos de entrada")

# O capturar todos
except Exception as e:
    print(f"Error inesperado: {e}")
```

**Usar tupla para múltiples tipos**

<!-- 
NOTAS DEL ORADOR:
- Agrupar errores que se manejan igual.
- `Exception` es la clase base. Captura casi todo. Usar con cuidado al final (catch-all).
-->

---

<!-- _header: 'Bloque else' -->

# else: cuando no hay error

```python
try:
    edad = int(input("Edad: "))
except ValueError:
    print("Edad inválida")
else:
    # Solo se ejecuta si NO hubo error
    print(f"Edad válida: {edad}")
    if edad >= 18:
        print("Sos mayor de edad")
```

**else se ejecuta si try funciona**

<!-- 
NOTAS DEL ORADOR:
- ¿Por qué no ponerlo dentro del `try`?
- Para mantener el bloque `try` pequeño y enfocado solo en lo que puede fallar.
- "Try to do this... if it worked (else), do that".
-->

---

<!-- _header: 'Bloque finally' -->

# finally: siempre se ejecuta

```python
archivo = None
try:
    archivo = open("datos.txt", "r")
    contenido = archivo.read()
    print(contenido)
except FileNotFoundError:
    print("Archivo no encontrado")
finally:
    # SIEMPRE se ejecuta
    if archivo:
        archivo.close()
        print("Archivo cerrado")
```

**finally para limpieza**

<!-- 
NOTAS DEL ORADOR:
- Garantiza que se ejecute incluso si hay error o si hay un `return` dentro del try.
- Clave para liberar recursos (archivos, conexiones).
-->

---

<!-- _header: 'Estructura completa' -->

# try-except-else-finally

```python
try:
    # Intentar esto
    numero = int(input("Número: "))
    resultado = 100 / numero
except ValueError:
    # Si hay error de valor
    print("No es un número")
except ZeroDivisionError:
    # Si hay división por 0
    print("No dividir por 0")
else:
    # Si todo salió bien
    print(f"Resultado: {resultado}")
finally:
    # Siempre ejecutar
    print("Operación finalizada")
```

<!-- 
NOTAS DEL ORADOR:
- Mapa completo del flujo.
-->

---

<!-- _header: 'Orden de ejecución' -->

# Flujo de control

**Caso exitoso:**
```
try → else → finally
```

**Caso con error capturado:**
```
try (parcial) → except → finally
```

**Caso con error NO capturado:**
```
try (parcial) → finally → Crash
```

<!-- 
NOTAS DEL ORADOR:
- Notar que `finally` se ejecuta incluso antes del Crash final.
-->

---

<!-- _header: 'Excepciones anidadas' -->

# try dentro de try

```python
try:
    nombre = input("Nombre: ")
    try:
        edad = int(input("Edad: "))
    except ValueError:
        print("Edad inválida, usando 0")
        edad = 0
    
    print(f"{nombre} tiene {edad} años")
except KeyboardInterrupt:
    print("\nOperación cancelada")
```

**Posible pero mejor evitar**

<!-- 
NOTAS DEL ORADOR:
- Aumenta la complejidad ciclomática.
- Mejor extraer a funciones separadas.
-->

---

<!-- _header: 'Ejemplo práctico' -->

# Calculadora robusta

```python
def calculadora():
    """Calculadora con manejo de errores."""
    try:
        a = float(input("Primer número: "))
        op = input("Operación (+, -, *, /): ")
        b = float(input("Segundo número: "))
        
        if op == "+":
            resultado = a + b
        elif op == "-":
            resultado = a - b
        elif op == "*":
            resultado = a * b
        elif op == "/":
            resultado = a / b
        else:
            print("Operación inválida")
            return
            
    except ValueError:
        print("Error: Ingresá números válidos")
    except ZeroDivisionError:
        print("Error: No se puede dividir por 0")
    else:
        print(f"Resultado: {resultado}")
    finally:
        print("Gracias por usar la calculadora")

calculadora()
```

<!-- 
NOTAS DEL ORADOR:
- Ejemplo integrador.
-->

---

<!-- _header: 'Ejercicio' -->

# Leer archivo seguro

**Crea una función que:**
1. Intente abrir archivo
2. Lea contenido
3. Maneje FileNotFoundError
4. Siempre cierre archivo (finally)
5. Devuelva contenido o None

<!-- 
NOTAS DEL ORADOR:
- Introducción al manejo de archivos (que veremos en detalle luego, pero es el caso clásico de excepciones).
-->

---

<!-- _header: 'Ejercicio - Solución' -->

# Posible solución

```python
def leer_archivo_seguro(nombre):
    """Lee archivo con manejo de errores."""
    archivo = None
    try:
        archivo = open(nombre, "r")
        contenido = archivo.read()
        return contenido
    except FileNotFoundError:
        print(f"Archivo {nombre} no encontrado")
        return None
    finally:
        if archivo:
            archivo.close()

# Usar
contenido = leer_archivo_seguro("datos.txt")
if contenido:
    print(contenido)
```

---

<!-- _header: 'Resumen' -->

# Para recordar

**Estructura:**
* `try` → código a intentar
* `except` → capturar error
* `else` → si no hay error
* `finally` → siempre ejecutar

**Múltiples except:**
* Específicos primero
* Generales después

**Capturar mensaje:**
* `except Tipo as e`

**Próximo:**
* raise: lanzar excepciones

<!-- 
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?
