---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Módulos - Parte 2/3' -->

# <!-- fit --> random
## Números y elecciones aleatorias
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Aprender a generar comportamiento no determinista.
- Gancho: "¿Cómo hacemos un juego divertido si la computadora siempre hace exactamente lo mismo? Necesitamos un poco de caos controlado."
-->

---

<!-- _header: 'Módulo random' -->

# Importar random

**Para usar random, importarlo:**
```python
import random

# O importar funciones específicas
from random import randint, choice
```

**Proporciona:**
* Números aleatorios
* Elecciones aleatorias
* Mezclar listas
* Simulaciones

<!--
NOTAS DEL ORADOR:
- Pseudo-aleatorio (PRNG): No es azar "real" (como desintegración atómica), es un algoritmo matemático muy complejo.
- Suficiente para juegos y simulaciones, NO para criptografía segura (para eso usar el módulo `secrets`).
-->

---

<!-- _header: 'Enteros aleatorios' -->

# randint: entero en rango

```python
import random

# Número entre 1 y 6 (dado)
dado = random.randint(1, 6)
print(dado)

# Número entre 0 y 100
numero = random.randint(0, 100)

# Ambos extremos son INCLUSIVOS
```

**Uso típico:** dados, juegos, simulaciones

<!--
NOTAS DEL ORADOR:
- ¡Atención! A diferencia de `range()`, aquí el extremo superior SÍ está incluido.
- `randint(1, 6)` puede dar 6.
-->

---

<!-- _header: 'Flotantes aleatorios' -->

# random: flotante 0-1

```python
import random

# Número entre 0.0 y 1.0
valor = random.random()
print(valor)  # Ej: 0.847362...

# Escalar a rango deseado
# Entre 0 y 100
precio = random.random() * 100

# Entre 50 y 150
precio = 50 + random.random() * 100
```

<!--
NOTAS DEL ORADOR:
- La base de casi todos los generadores.
- Devuelve un float en [0.0, 1.0). El 1.0 está excluido.
-->

---

<!-- _header: 'Flotante en rango' -->

# uniform: flotante en rango

```python
import random

# Flotante entre 1.5 y 5.5
temperatura = random.uniform(1.5, 5.5)
print(temperatura)  # Ej: 3.742...

# Flotante entre -10 y 10
valor = random.uniform(-10, 10)
```

**Más cómodo que random() con matemática**

<!--
NOTAS DEL ORADOR:
- Distribución uniforme: Todos los números tienen la misma probabilidad de salir.
-->

---

<!-- _header: 'Elegir de lista' -->

# choice: elemento aleatorio

```python
import random

# Elegir color
colores = ["rojo", "azul", "verde", "amarillo"]
color = random.choice(colores)
print(color)

# Elegir jugador
jugadores = ["Ana", "Juan", "María"]
turno = random.choice(jugadores)

# Lanzar moneda
moneda = random.choice(["cara", "cruz"])
```

<!--
NOTAS DEL ORADOR:
- Funciona con cualquier secuencia (listas, tuplas, strings).
- `random.choice("AEIOU")` te da una vocal.
-->

---

<!-- _header: 'Múltiples elecciones' -->

# choices: varios elementos (con repetición)

```python
import random

datos = [1, 2, 3, 4, 5]

# Elegir 3 elementos (pueden repetirse)
muestra = random.choices(datos, k=3)
print(muestra)  # Ej: [2, 2, 5]
```

**choices permite repetición**

<!--
NOTAS DEL ORADOR:
- Muestreo con reemplazo (como sacar una bolilla, mirarla y volverla a meter).
-->

---

<!-- _header: 'Muestra sin repetición' -->

# sample: sin repetición

```python
import random

numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Elegir 3 SIN repetición
muestra = random.sample(numeros, k=3)
print(muestra)  # Ej: [7, 2, 9]

# Sorteo de lotería
loteria = random.sample(range(1, 50), k=6)
```

**sample NO permite repetición**

<!--
NOTAS DEL ORADOR:
- Muestreo sin reemplazo (como repartir cartas).
- `k` no puede ser mayor que la población.
-->

---

<!-- _header: 'Mezclar lista' -->

# shuffle: mezclar in-place

```python
import random

# Mazo de cartas
cartas = ["A", "2", "3", "4", "5"]
print(cartas)  # ["A", "2", "3", "4", "5"]

# Mezclar (modifica la lista)
random.shuffle(cartas)
print(cartas)  # Ej: ["3", "A", "5", "2", "4"]
```

**shuffle modifica la lista original**

<!--
NOTAS DEL ORADOR:
- ¡Ojo! Devuelve `None`.
- Error común: `cartas_mezcladas = random.shuffle(cartas)` (cartas_mezcladas valdrá None).
-->

---

<!-- _header: 'Semilla' -->

# seed: reproducibilidad

```python
import random

# Sin semilla: aleatorio cada vez
print(random.randint(1, 10))  # Diferente cada vez

# Con semilla: mismo resultado
random.seed(42)
print(random.randint(1, 10))  # Siempre igual

random.seed(42)
print(random.randint(1, 10))  # Mismo resultado
```

**Útil para testing y debugging**

<!--
NOTAS DEL ORADOR:
- Vital para la ciencia de datos y debugging.
- Permite que "el azar" sea repetible.
-->

---

<!-- _header: 'Ejemplo: Dado' -->

# Simulador de dados

```python
import random

def tirar_dado():
    """Simula tirar un dado de 6 caras."""
    return random.randint(1, 6)

def tirar_dos_dados():
    """Simula tirar dos dados."""
    dado1 = tirar_dado()
    dado2 = tirar_dado()
    total = dado1 + dado2
    return dado1, dado2, total

# Jugar
d1, d2, suma = tirar_dos_dados()
print(f"Dado 1: {d1}")
print(f"Dado 2: {d2}")
print(f"Total: {suma}")
```

---

<!-- _header: 'Ejemplo: Contraseña' -->

# Generador de contraseñas

```python
import random

def generar_contraseña(longitud=8):
    """Genera contraseña aleatoria."""
    caracteres = "abcdefghijklmnopqrstuvwxyz"
    caracteres += "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    caracteres += "0123456789"
    caracteres += "!@#$%&*"
    
    # Elegir caracteres aleatorios
    password = ""
    for _ in range(longitud):
        password += random.choice(caracteres)
    
    return password

print(generar_contraseña(12))
# Ej: "aB5!xZ2@mK9p"
```

---

<!-- _header: 'Ejemplo: Juego' -->

# Adivinar número

```python
import random

def juego_adivinar():
    """Juego de adivinar número."""
    secreto = random.randint(1, 100)
    intentos = 0
    
    print("¡Adivina el número entre 1 y 100!")
    
    while True:
        intento = int(input("Tu número: "))
        intentos += 1
        
        if intento < secreto:
            print("Muy bajo")
        elif intento > secreto:
            print("Muy alto")
        else:
            print(f"¡Correcto! En {intentos} intentos")
            break

juego_adivinar()
```

---

<!-- _header: 'Ejemplo: Sorteo' -->

# Sistema de sorteo

```python
import random

def sorteo(participantes, premios=1):
    """Realiza sorteo entre participantes."""
    if premios > len(participantes):
        print("No hay suficientes participantes")
        return []
    
    ganadores = random.sample(participantes, k=premios)
    return ganadores

# Uso
inscriptos = ["Ana", "Juan", "María", "Pedro", "Lucía"]
ganadores = sorteo(inscriptos, premios=2)

print("¡Ganadores!")
for i, ganador in enumerate(ganadores, 1):
    print(f"{i}. {ganador}")
```

---

<!-- _header: 'Distribuciones' -->

# Otras distribuciones

```python
import random

# Gaussiana (normal)
# Media 100, desviación 15
iq = random.gauss(100, 15)

# Exponencial
tiempo = random.expovariate(1.5)

# Beta
valor = random.betavariate(2, 5)
```

**Para simulaciones avanzadas**

<!--
NOTAS DEL ORADOR:
- Mencionar solo si hay interés en estadística.
- La distribución "normal" (campana) es la más común en la naturaleza.
-->

---

<!-- _header: 'Ejercicio' -->

# Simulador de monedas

**Crea un programa que:**
1. Simule lanzar una moneda N veces
2. Cuente cuántas caras y cruces
3. Calcule porcentaje de cada uno
4. Muestre resultados

---

<!-- _header: 'Ejercicio - Solución' -->

# Posible solución

```python
import random

def simular_monedas(n):
    """Simula lanzar moneda n veces."""
    caras = 0
    cruces = 0
    
    for _ in range(n):
        resultado = random.choice(["cara", "cruz"])
        if resultado == "cara":
            caras += 1
        else:
            cruces += 1
    
    print(f"Lanzamientos: {n}")
    print(f"Caras: {caras} ({caras/n*100:.1f}%)")
    print(f"Cruces: {cruces} ({cruces/n*100:.1f}%)")

simular_monedas(1000)
```

---

<!-- _header: 'Referencia rápida' -->

# Funciones principales

**Enteros:**
* `randint(a, b)` - entero entre a y b (inclusivo)

**Flotantes:**
* `random()` - flotante entre 0 y 1
* `uniform(a, b)` - flotante entre a y b

**Secuencias:**
* `choice(seq)` - un elemento
* `sample(seq, k)` - k sin repetir
* `shuffle(seq)` - mezclar lista

---

<!-- _header: 'Resumen' -->

# Para recordar

**random:**
* Importar: `import random`
* Enteros: `randint()`
* Flotantes: `random()`, `uniform()`
* Elegir: `choice()`, `sample()`
* Mezclar: `shuffle()`

**Aplicaciones:**
* Juegos
* Simulaciones
* Sorteos
* Muestreo

**Próximo:**
* Módulo math

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?