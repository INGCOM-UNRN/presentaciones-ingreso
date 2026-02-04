---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Módulos - Parte 3/3' -->

# <!-- fit --> math
## Matemática avanzada
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Conocer la caja de herramientas matemáticas de Python.
- Gancho: "¿Necesitan calcular la hipotenusa de un triángulo o el seno de un ángulo? No escriban la fórmula, ya está hecha."
-->

---

<!-- _header: 'Módulo math' -->

# Importar math

**Para operaciones matemáticas:**
```python
import math

# O importar funciones específicas
from math import sqrt, pi, sin
```

**Proporciona:**
* Funciones trigonométricas
* Logaritmos y exponenciales
* Constantes matemáticas
* Redondeo y truncado

<!--
NOTAS DEL ORADOR:
- Funciones C-style optimizadas.
- Si necesitan matemática compleja (matrices, álgebra lineal), usarán `numpy` en el futuro, pero `math` es la base.
-->

---

<!-- _header: 'Constantes' -->

# Constantes matemáticas

```python
import math

# Pi
print(math.pi)      # 3.141592653589793

# Euler
print(math.e)       # 2.718281828459045

# Tau (2π)
print(math.tau)     # 6.283185307179586

# Infinito
print(math.inf)     # inf
print(-math.inf)    # -inf
```

<!--
NOTAS DEL ORADOR:
- Usar `math.pi` es mucho mejor que escribir `3.14159` manualmente (más preciso y menos error humano).
- `math.inf` es útil para inicializar algoritmos de búsqueda de mínimos (empezar con infinito y bajar).
-->

---

<!-- _header: 'Potencias y raíces' -->

# Operaciones básicas

```python
import math

# Raíz cuadrada
print(math.sqrt(16))      # 4.0
print(math.sqrt(2))       # 1.414...

# Potencia
print(math.pow(2, 3))     # 8.0
print(2 ** 3)             # 8 (también funciona)

# Raíz cúbica (Python 3.11+)
print(math.cbrt(27))      # 3.0
```

<!--
NOTAS DEL ORADOR:
- `math.pow` siempre devuelve float. `**` devuelve int si ambos son int.
- `sqrt` es mucho más legible que `x ** 0.5`.
-->

---

<!-- _header: 'Redondeo' -->

# Funciones de redondeo

```python
import math

x = 3.7

# Techo (redondear arriba)
print(math.ceil(x))     # 4

# Piso (redondear abajo)
print(math.floor(x))    # 3

# Truncar (eliminar decimales)
print(math.trunc(x))    # 3

# Comparar con round()
print(round(x))         # 4
```

<!--
NOTAS DEL ORADOR:
- Diferencia sutil pero importante:
    - `round()` va al más cercano.
    - `floor()` siempre baja.
    - `ceil()` siempre sube.
    - `trunc()` corta (para positivos es igual a floor, para negativos igual a ceil).
-->

---

<!-- _header: 'Valor absoluto' -->

# Módulo y signo

```python
import math

# Valor absoluto
print(math.fabs(-5))      # 5.0
print(abs(-5))            # 5 (también funciona)

# Copiar signo
print(math.copysign(5, -1))   # -5.0
print(math.copysign(-5, 1))   # 5.0
```

<!--
NOTAS DEL ORADOR:
- `abs()` es built-in (no requiere import). `math.fabs()` siempre devuelve float.
-->

---

<!-- _header: 'Logaritmos' -->

# Funciones logarítmicas

```python
import math

# Logaritmo natural (base e)
print(math.log(math.e))     # 1.0
print(math.log(10))         # 2.302...

# Logaritmo base 10
print(math.log10(100))      # 2.0
print(math.log10(1000))     # 3.0

# Logaritmo base 2
print(math.log2(8))         # 3.0
print(math.log2(1024))      # 10.0

# Logaritmo base arbitraria
print(math.log(81, 3))      # 4.0 (3^4 = 81)
```

<!--
NOTAS DEL ORADOR:
- `log` sin base es logaritmo natural (ln).
- `log2` es fundamental en informática (bits, entropía).
-->

---

<!-- _header: 'Exponenciales' -->

# Funciones exponenciales

```python
import math

# e^x
print(math.exp(1))          # 2.718... (e)
print(math.exp(2))          # 7.389...

# 2^x
print(math.exp2(3))         # 8.0
print(math.exp2(10))        # 1024.0
```

<!--
NOTAS DEL ORADOR:
- Inversas de los logaritmos.
-->

---

<!-- _header: 'Trigonometría' -->

# Funciones trigonométricas

```python
import math

# Seno, coseno, tangente (en radianes)
angulo = math.pi / 4  # 45 grados

print(math.sin(angulo))     # 0.707...
print(math.cos(angulo))     # 0.707...
print(math.tan(angulo))     # 1.0

# Conversión grados ↔ radianes
grados = 90
radianes = math.radians(grados)
print(math.sin(radianes))   # 1.0

print(math.degrees(math.pi))  # 180.0
```

<!--
NOTAS DEL ORADOR:
- ¡CUIDADO! Las funciones trigonométricas esperan RADIANES, no grados.
- Siempre usar `math.radians()` si se piensa en grados.
-->

---

<!-- _header: 'Trigonometría inversa' -->

# Arco seno, coseno, tangente

```python
import math

# Funciones inversas (devuelven radianes)
print(math.asin(1))         # π/2
print(math.acos(0))         # π/2
print(math.atan(1))         # π/4

# atan2 (considera cuadrante)
print(math.atan2(1, 1))     # π/4
```

<!--
NOTAS DEL ORADOR:
- `atan2(y, x)` es superior a `atan(y/x)` porque maneja correctamente los cuadrantes y la división por cero.
-->

---

<!-- _header: 'Hiperbólicas' -->

# Funciones hiperbólicas

```python
import math

x = 1.0

# Seno, coseno, tangente hiperbólicos
print(math.sinh(x))
print(math.cosh(x))
print(math.tanh(x))

# Inversas
print(math.asinh(x))
print(math.acosh(x))
print(math.atanh(0.5))
```

<!--
NOTAS DEL ORADOR:
- Útil en ingeniería y física.
-->

---

<!-- _header: 'Factoriales' -->

# Factorial y combinatoria

```python
import math

# Factorial
print(math.factorial(5))    # 120 (5! = 5×4×3×2×1)
print(math.factorial(0))    # 1 (por definición)

# Combinaciones (n sobre k)
print(math.comb(5, 2))      # 10 (5!/(2!×3!))

# Permutaciones
print(math.perm(5, 2))      # 20 (5!/(5-2)!)
```

<!--
NOTAS DEL ORADOR:
- Estadística y probabilidad.
-->

---

<!-- _header: 'GCD y LCM' -->

# Máximo común divisor

```python
import math

# MCD (Greatest Common Divisor)
print(math.gcd(48, 18))     # 6
print(math.gcd(100, 50))    # 50

# MCD de múltiples números
print(math.gcd(12, 18, 24)) # 6

# MCM (Least Common Multiple) - Python 3.9+
print(math.lcm(4, 6))       # 12
print(math.lcm(12, 18, 24)) # 72
```

<!--
NOTAS DEL ORADOR:
- Teoría de números.
-->

---

<!-- _header: 'Distancias' -->

# Distancia y magnitud

```python
import math

# Distancia euclidiana
x1, y1 = 0, 0
x2, y2 = 3, 4

distancia = math.sqrt((x2-x1)**2 + (y2-y1)**2)
print(distancia)  # 5.0

# O usar hypot (más preciso)
distancia = math.hypot(x2-x1, y2-y1)
print(distancia)  # 5.0

# Distancia 3D
d = math.hypot(3, 4, 12)
print(d)  # 13.0
```

<!--
NOTAS DEL ORADOR:
- `hypot` evita problemas de desbordamiento (overflow) al elevar al cuadrado números muy grandes.
-->

---

<!-- _header: 'Ejemplo: Círculo' -->

# Cálculos con círculos

```python
import math

def calcular_circulo(radio):
    """Calcula área y perímetro de círculo."""
    area = math.pi * radio ** 2
    perimetro = 2 * math.pi * radio
    return area, perimetro

# Usar
radio = 5
area, perimetro = calcular_circulo(radio)
print(f"Radio: {radio}")
print(f"Área: {area:.2f}")
print(f"Perímetro: {perimetro:.2f}")
```

---

<!-- _header: 'Ejemplo: Hipotenusa' -->

# Teorema de Pitágoras

```python
import math

def hipotenusa(cateto1, cateto2):
    """Calcula hipotenusa de triángulo rectángulo."""
    return math.hypot(cateto1, cateto2)

def es_triangulo_rectangulo(a, b, c):
    """Verifica si es triángulo rectángulo."""
    lados = sorted([a, b, c])
    esperado = math.hypot(lados[0], lados[1])
    return math.isclose(esperado, lados[2])

# Usar
print(hipotenusa(3, 4))  # 5.0
print(es_triangulo_rectangulo(3, 4, 5))  # True
```

<!--
NOTAS DEL ORADOR:
- `math.isclose` es fundamental al comparar flotantes. Nunca usar `==` con floats por errores de precisión.
-->

---

<!-- _header: 'Ejemplo: Interés compuesto' -->

# Fórmula de interés

```python
import math

def interes_compuesto(capital, tasa, tiempo, frecuencia=12):
    """
    Calcula interés compuesto.
    
    capital: Monto inicial
    tasa: Tasa anual (ej: 0.05 para 5%)
    tiempo: Años
    frecuencia: Veces al año (12=mensual)
    """
    monto = capital * math.pow(
        1 + tasa/frecuencia,
        frecuencia * tiempo
    )
    return monto

# $1000 al 5% anual por 10 años
final = interes_compuesto(1000, 0.05, 10)
print(f"Monto final: ${final:.2f}")
```

---

<!-- _header: 'Verificaciones' -->

# Funciones de verificación

```python
import math

# Verificar si es finito
print(math.isfinite(100))       # True
print(math.isfinite(math.inf))  # False

# Verificar si es infinito
print(math.isinf(math.inf))     # True

# Verificar si es NaN
print(math.isnan(float('nan'))) # True

# Comparar flotantes
print(math.isclose(0.1 + 0.2, 0.3))  # True
```

<!--
NOTAS DEL ORADOR:
- NaN = Not a Number (resultado de operaciones inválidas como 0/0 o inf-inf).
- `math.isclose` es la forma correcta de comprobar igualdad de flotantes.
-->

---

<!-- _header: 'Ejercicio' -->

# Calculadora científica

**Crea funciones para:**
1. Convertir grados a radianes
2. Calcular seno, coseno, tangente en grados
3. Calcular área de triángulo (fórmula de Herón)
4. Calcular distancia entre dos puntos

---

<!-- _header: 'Ejercicio - Solución' -->

# Posible solución (parte 1)

```python
import math

def grados_a_radianes(grados):
    """Convierte grados a radianes."""
    return math.radians(grados)

def seno_grados(grados):
    """Calcula seno de ángulo en grados."""
    return math.sin(math.radians(grados))

def coseno_grados(grados):
    """Calcula coseno de ángulo en grados."""
    return math.cos(math.radians(grados))

def tangente_grados(grados):
    """Calcula tangente de ángulo en grados."""
    return math.tan(math.radians(grados))
```

---

<!-- _header: 'Ejercicio - Solución' -->

# Posible solución (parte 2)

```python
def area_triangulo_heron(a, b, c):
    """Calcula área con fórmula de Herón."""
    s = (a + b + c) / 2  # Semiperímetro
    area = math.sqrt(s * (s-a) * (s-b) * (s-c))
    return area

def distancia_puntos(x1, y1, x2, y2):
    """Calcula distancia entre dos puntos."""
    return math.hypot(x2-x1, y2-y1)

# Probar
print(seno_grados(90))  # 1.0
print(area_triangulo_heron(3, 4, 5))  # 6.0
print(distancia_puntos(0, 0, 3, 4))  # 5.0
```

---

<!-- _header: 'Referencia rápida' -->

# Funciones principales

**Constantes:** `pi`, `e`, `tau`, `inf`
**Redondeo:** `ceil()`, `floor()`, `trunc()`
**Potencias:** `sqrt()`, `pow()`, `exp()`
**Logaritmos:** `log()`, `log10()`, `log2()`
**Trigonometría:** `sin()`, `cos()`, `tan()`
**Conversión:** `radians()`, `degrees()`
**Otros:** `factorial()`, `gcd()`, `hypot()`

---

<!-- _header: 'Resumen' -->

# Para recordar

**math:**
* Importar: `import math`
* Constantes: π, e, ∞
* Funciones básicas: sqrt, pow, abs
* Redondeo: ceil, floor, trunc
* Trigonometría: sin, cos, tan
* Logaritmos: log, log10, log2

**Aplicaciones:**
* Cálculos científicos
* Geometría
* Finanzas
* Física

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: inverse -->

# <!-- fit --> ¡Módulos completos!
## str, random, math

---

<!-- _class: centered -->

# ¿Preguntas?