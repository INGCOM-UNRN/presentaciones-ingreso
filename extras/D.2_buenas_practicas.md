---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Estilo - Parte 2/2' -->

# <!-- fit --> Buenas Prácticas
## Código profesional
Curso de Ingreso - Ingeniería en Computación

<!-- 
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Elevar el nivel de "escribir código que funciona" a "escribir código de calidad".
- Gancho: "¿Saben la diferencia entre un amateur y un profesional? El amateur escribe código para que la computadora entienda. El profesional escribe código para que otros humanos entiendan."
-->

---

<!-- _header: 'Principio DRY' -->

# Don't Repeat Yourself

**No repetir código:**
```python
# ❌ Repetitivo
area1 = base1 * altura1
area2 = base2 * altura2
area3 = base3 * altura3

# ✅ Usar función
def calcular_area(base, altura):
    return base * altura

area1 = calcular_area(base1, altura1)
area2 = calcular_area(base2, altura2)
area3 = calcular_area(base3, altura3)
```

<!--
NOTAS DEL ORADOR:
- "No te repitas".
- Si copiás y pegás código, estás creando deuda técnica.
- Si hay un error en la lógica, tenés que arreglarlo en N lugares.
-->

---

<!-- _header: 'Funciones pequeñas' -->

# Una responsabilidad por función

**Dividir tareas complejas:**
```python
# ❌ Función que hace demasiado
def procesar_todo(datos):
    # Validar (20 líneas)
    # Transformar (30 líneas)
    # Guardar (15 líneas)
    # Notificar (10 líneas)
    pass

# ✅ Dividir responsabilidades
def validar_datos(datos):
    pass

def transformar_datos(datos):
    pass

def guardar_datos(datos):
    pass

def notificar_exito():
    pass
```

<!--
NOTAS DEL ORADOR:
- Principio de Responsabilidad Única (SRP).
- Una función debe hacer UNA cosa y hacerla bien.
- Facilita el testing y la reutilización.
-->

---

<!-- _header: 'Nombres descriptivos' -->

# Nombres que explican

**Variables:**
```python
# ❌ Nombres crípticos
x = 25
t = 3600
c = "rgb(255,0,0)"

# ✅ Nombres claros
edad_usuario = 25
tiempo_espera_segundos = 3600
color_error = "rgb(255,0,0)"
```

**Funciones:**
```python
# ❌ Poco claro
def proc(d):
    pass

# ✅ Descriptivo
def procesar_pedido(datos_pedido):
    pass
```

<!--
NOTAS DEL ORADOR:
- El código autodocumentado es mejor que los comentarios.
- Si una variable se llama `tiempo_espera_segundos`, no necesito un comentario que diga `# Tiempo en segundos`.
-->

---

<!-- _header: 'Valores mágicos' -->

# Evitar números literales

**Usar constantes:**
```python
# ❌ Números "mágicos"
if edad >= 18:
    pass

if intentos > 3:
    pass

precio = cantidad * 1.21

# ✅ Constantes con nombre
EDAD_MAYOR = 18
MAX_INTENTOS = 3
IVA = 1.21

if edad >= EDAD_MAYOR:
    pass

precio = cantidad * IVA
```

<!--
NOTAS DEL ORADOR:
- Un "número mágico" es un literal numérico en medio del código sin explicación.
- Las constantes centralizan la configuración. Si el IVA cambia, solo toco una línea.
-->

---

<!-- _header: 'Valores por defecto' -->

# Parámetros opcionales

**Valores predeterminados sensatos:**
```python
def crear_usuario(nombre, edad, activo=True, rol="usuario"):
    """
    Crea usuario con valores por defecto.
    
    Args:
        nombre: Nombre del usuario (requerido)
        edad: Edad del usuario (requerido)
        activo: Si está activo (default: True)
        rol: Rol del usuario (default: "usuario")
    """
    return {
        "nombre": nombre,
        "edad": edad,
        "activo": activo,
        "rol": rol
    }

# Uso simple
usuario = crear_usuario("Ana", 25)

# Personalizar
admin = crear_usuario("Juan", 30, rol="admin")
```

<!--
NOTAS DEL ORADOR:
- Flexibilidad sin complejidad.
- El 90% de los casos usa el default, el 10% restante tiene el poder de cambiarlo.
-->

---

<!-- _header: 'Retornar temprano' -->

# Early return

**Evitar anidamiento profundo:**
```python
# ❌ Anidamiento profundo
def procesar(datos):
    if datos:
        if datos.validos():
            if datos.completos():
                # Lógica principal
                return resultado
            else:
                return None
        else:
            return None
    else:
        return None

# ✅ Retornar temprano
def procesar(datos):
    if not datos:
        return None
    
    if not datos.validos():
        return None
    
    if not datos.completos():
        return None
    
    # Lógica principal sin anidamiento
    return resultado
```

<!--
NOTAS DEL ORADOR:
- También llamado "Guard Clauses".
- Reduce la carga cognitiva. Una vez que pasás un `if`, te olvidás de ese caso.
-->

---

<!-- _header: 'Validar entradas' -->

# Defensivo desde el inicio

**Verificar precondiciones:**
```python
def dividir(a, b):
    """Divide dos números con validación."""
    # Validar tipos
    if not isinstance(a, (int, float)):
        raise TypeError("a debe ser número")
    
    if not isinstance(b, (int, float)):
        raise TypeError("b debe ser número")
    
    # Validar valores
    if b == 0:
        raise ValueError("No se puede dividir por 0")
    
    return a / b
```

<!--
NOTAS DEL ORADOR:
- Fail Fast: Si los datos están mal, explota ahora, no dentro de 100 líneas con un error raro.
-->

---

<!-- _header: 'Evitar variables globales' -->

# Pasar datos como parámetros

**Funciones puras preferibles:**
```python
# ❌ Variables globales
contador = 0

def incrementar():
    global contador
    contador += 1

# ✅ Pasar como parámetro
def incrementar(contador):
    return contador + 1

contador = 0
contador = incrementar(contador)
```

<!--
NOTAS DEL ORADOR:
- Las variables globales crean dependencias ocultas y hacen el código difícil de testear y paralelizar.
-->

---

<!-- _header: 'Estructura clara' -->

# Organizar el código

**Orden lógico:**
```python
"""
Módulo para gestión de usuarios.

Este módulo proporciona funciones para crear,
validar y gestionar usuarios del sistema.
"""

# 1. Imports
import math
import random

# 2. Constantes
MAX_INTENTOS = 3
EDAD_MINIMA = 18

# 3. Funciones auxiliares
def validar_edad(edad):
    pass

# 4. Funciones principales
def crear_usuario(nombre, edad):
    pass

# 5. Código principal
if __name__ == "__main__":
    # Ejecutar solo si es script principal
    pass
```

<!--
NOTAS DEL ORADOR:
- Estructura estándar de un script Python.
- El bloque `if __name__ == "__main__":` permite que el archivo sea importado como módulo o ejecutado como script.
-->

---

<!-- _header: 'Manejo de errores' -->

# Excepciones específicas

**Capturar errores apropiados:**
```python
# ❌ Muy genérico
try:
    procesar_datos()
except:
    print("Error")

# ✅ Específico
try:
    procesar_datos()
except FileNotFoundError:
    print("Archivo no encontrado")
except ValueError as e:
    print(f"Datos inválidos: {e}")
except Exception as e:
    print(f"Error inesperado: {e}")
    raise  # Re-lanzar si es crítico
```

<!--
NOTAS DEL ORADOR:
- Capturar solo lo que sabés manejar.
-->

---

<!-- _header: 'Comentarios útiles' -->

# Cuándo comentar

**Comentar el por qué:**
```python
# ❌ Comentario obvio
i = i + 1  # Incrementar i

# ✅ Explicar decisión
# Incrementar para compensar índice base-1
# usado por la API externa
i = i + 1

# ✅ Advertir
# CUIDADO: Esta función modifica la lista original
# para mejorar performance con listas grandes
def ordenar_inplace(lista):
    pass

# ✅ TODO para tareas pendientes
# TODO: Optimizar usando búsqueda binaria
def buscar_lento(lista, valor):
    pass
```

<!--
NOTAS DEL ORADOR:
- Los comentarios mienten (porque el código cambia y el comentario no). El código nunca miente.
-->

---

<!-- _header: 'Testing' -->

# Escribir tests

**Verificar comportamiento:**
```python
def sumar(a, b):
    """Suma dos números."""
    return a + b

# Tests
def test_sumar_positivos():
    assert sumar(2, 3) == 5

def test_sumar_negativos():
    assert sumar(-2, -3) == -5

def test_sumar_cero():
    assert sumar(5, 0) == 5

def test_sumar_flotantes():
    resultado = sumar(0.1, 0.2)
    assert abs(resultado - 0.3) < 0.0001
```

<!--
NOTAS DEL ORADOR:
- TDD (Test Driven Development).
- Escribir tests te da confianza para refactorizar.
-->

---

<!-- _header: 'Documentación' -->

# Docstrings completos

**Estilo Google:**
```python
def calcular_descuento(precio, porcentaje):
    """
    Calcula precio con descuento aplicado.
    
    Args:
        precio (float): Precio original del producto
        porcentaje (float): Porcentaje de descuento (0-100)
        
    Returns:
        float: Precio final con descuento aplicado
        
    Raises:
        ValueError: Si precio es negativo
        ValueError: Si porcentaje no está en rango [0, 100]
        
    Example:
        >>> calcular_descuento(100, 20)
        80.0
    """
    if precio < 0:
        raise ValueError("Precio no puede ser negativo")
    
    if not 0 <= porcentaje <= 100:
        raise ValueError("Porcentaje debe estar entre 0 y 100")
    
    descuento = precio * (porcentaje / 100)
    return precio - descuento
```

<!--
NOTAS DEL ORADOR:
- Documentación profesional.
-->

---

<!-- _header: 'Inmutabilidad' -->

# Preferir datos inmutables

**Evitar modificaciones inesperadas:**
```python
# ❌ Modificar parámetro
def agregar_elemento(lista, elemento):
    lista.append(elemento)
    return lista

# ✅ Crear nueva lista
def agregar_elemento(lista, elemento):
    return lista + [elemento]

# ✅ O dejar claro que modifica
def agregar_elemento_inplace(lista, elemento):
    """ATENCIÓN: Modifica lista original."""
    lista.append(elemento)
```

<!--
NOTAS DEL ORADOR:
- Efectos secundarios. Si modificás una lista que te pasaron, podés romper el código de quien te llamó.
-->

---

<!-- _header: 'Comprehensions' -->

# Usar cuando simplifican

**List comprehensions:**
```python
# ✅ Claro y conciso
cuadrados = [x**2 for x in range(10)]

# ✅ Con filtro
pares= [x for x in numeros if x % 2 == 0]

# ❌ Demasiado complejo
resultado = [
    procesar(transformar(x)) 
    for x in datos 
    if validar(x) and verificar(x) 
    if cumple_condicion(x)
]

# ✅ Mejor con for tradicional cuando es complejo
resultado = []
for x in datos:
    if validar(x) and verificar(x):
        if cumple_condicion(x):
            resultado.append(procesar(transformar(x)))
```

<!--
NOTAS DEL ORADOR:
- "Clever" vs "Clear". Sé claro, no inteligente.
-->

---

<!-- _header: 'Context managers' -->

# Usar with para recursos

**Garantizar limpieza:**
```python
# ❌ Manual y propenso a errores
archivo = open("datos.txt")
try:
    datos = archivo.read()
finally:
    archivo.close()

# ✅ Context manager
with open("datos.txt") as archivo:
    datos = archivo.read()
# Se cierra automáticamente

# ✅ Múltiples recursos
with open("entrada.txt") as entrada, \
     open("salida.txt", "w") as salida:
    for linea in entrada:
        salida.write(procesar(linea))
```

<!--
NOTAS DEL ORADOR:
- Gestión de recursos segura y elegante.
-->

---

<!-- _header: 'Código defensivo' -->

# Anticipar problemas

**Validar asunciones:**
```python
def calcular_promedio(numeros):
    """Calcula promedio con validación."""
    # Validar tipo
    if not isinstance(numeros, list):
        raise TypeError("Se esperaba lista")
    
    # Validar no vacía
    if not numeros:
        raise ValueError("Lista vacía")
    
    # Validar elementos son números
    if not all(isinstance(x, (int, float)) for x in numeros):
        raise TypeError("Todos los elementos deben ser números")
    
    return sum(numeros) / len(numeros)
```

---

<!-- _header: 'Ejemplo completo' -->

# Aplicando buenas prácticas

```python
"""Gestor de inventario."""

# Constantes
STOCK_MINIMO = 10
PRECIO_BASE = 100.0

class ProductoAgotadoError(Exception):
    """Se lanzó cuando no hay stock."""
    pass


def validar_cantidad(cantidad):
    """Valida que cantidad sea válida."""
    if not isinstance(cantidad, int):
        raise TypeError("Cantidad debe ser entero")
    if cantidad < 0:
        raise ValueError("Cantidad no puede ser negativa")


def calcular_precio_final(precio_base, cantidad, descuento=0):
    """
    Calcula precio final con descuento.
    
    Args:
        precio_base: Precio unitario
        cantidad: Unidades a comprar
        descuento: Porcentaje descuento (0-100)
        
    Returns:
        float: Precio total con descuento
    """
    validar_cantidad(cantidad)
    
    if not 0 <= descuento <= 100:
        raise ValueError("Descuento debe estar entre 0 y 100")
    
    subtotal = precio_base * cantidad
    descuento_monto = subtotal * (descuento / 100)
    return subtotal - descuento_monto
```

---

<!-- _header: 'Checklist' -->

# Lista de verificación

**Antes de compartir código:**
- [ ] Nombres descriptivos
- [ ] Funciones pequeñas (< 20 líneas)
- [ ] Sin repetición (DRY)
- [ ] Manejo de errores apropiado
- [ ] Docstrings en funciones públicas
- [ ] Sin números mágicos
- [ ] Tests para funcionalidad crítica
- [ ] Sigue PEP 8
- [ ] Sin variables globales innecesarias
- [ ] Comentarios útiles (no obvios)

---

<!-- _class: inverse -->

# <!-- fit --> ¡Código limpio!
## Profesional y mantenible

---

<!-- _header: 'Resumen' -->

# Principios clave

**DRY:** No repetir código
**SRP:** Una responsabilidad por función
**Nombres:** Claros y descriptivos
**Validación:** Defensivo desde inicio
**Errores:** Manejar específicamente
**Tests:** Verificar comportamiento
**Documentación:** Explicar el por qué

**"El código es para humanos, no solo para máquinas"**

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?