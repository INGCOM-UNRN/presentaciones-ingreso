---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Rúbrica - Parte 1/1' -->

# <!-- fit --> Rúbrica de Evaluación
## Cómo se evalúa el código
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Transparentar el proceso de evaluación y establecer expectativas de calidad.
- Gancho: "¿Saben por qué les pedimos nombres descriptivos y docstrings? Porque en la vida real, el código se lee 10 veces más de lo que se escribe."
-->

---

<!-- _header: 'Filosofía' -->

# Más que funcionar

**No es suficiente que "funcione":**
* El código debe ser legible
* Debe estar bien estructurado
* Debe seguir buenas prácticas
* Debe mostrar comprensión

**"El código es para humanos"**

<!--
NOTAS DEL ORADOR:
- No somos una máquina que califica si el output es correcto. Somos humanos que evalúan el pensamiento algorítmico.
- Un código que funciona pero es ilegible es una "bomba de tiempo" técnica.
-->

---

<!-- _header: 'Dimensiones' -->

# 4 Dimensiones de evaluación

**1. Corrección Funcional (40%)**
* ¿Funciona correctamente?
* ¿Maneja casos especiales?

**2. Legibilidad y Estilo (30%)**
* ¿Es fácil de leer?
* ¿Sigue PEP 8?

**3. Diseño y Estructura (20%)**
* ¿Está bien organizado?
* ¿Usa funciones apropiadamente?

**4. Apropiación de Herramientas (10%)**
* ¿Usa herramientas aprendidas?

<!--
NOTAS DEL ORADOR:
- Notar que la "Corrección" es solo el 40%. Podés tener un programa que dé el resultado correcto pero igual no aprobar si el resto es un desastre.
- Queremos formar ingenieros, no solo "coders".
-->

---

<!-- _header: 'Dimensión 1' -->

# Corrección Funcional (40%)

**Qué se evalúa:**
* Programa funciona según enunciado
* Maneja entradas válidas
* Maneja casos borde
* Salidas correctas

**Niveles:**
* **Excelente:** Todo funciona, casos borde
* **Bueno:** Funciona en casos normales
* **Suficiente:** Funciona parcialmente
* **Insuficiente:** No funciona

<!--
NOTAS DEL ORADOR:
- "Casos borde": ¿Qué pasa si la lista está vacía? ¿Si el número es negativo?
- Robustez: ¿Se rompe ante el primer error?
-->

---

<!-- _header: 'Dimensión 2' -->

# Legibilidad y Estilo (30%)

**Qué se evalúa:**
* Nombres descriptivos
* Formato consistente (PEP 8)
* Comentarios útiles
* Código claro

**Niveles:**
* **Excelente:** Profesional, auto-documentado
* **Bueno:** Claro, sigue convenciones
* **Suficiente:** Legible con esfuerzo
* **Insuficiente:** Confuso, sin estilo

<!--
NOTAS DEL ORADOR:
- El código entra por los ojos.
- ¿Usaste snake_case? ¿Hay espacios alrededor de los operadores?
-->

---

<!-- _header: 'Dimensión 3' -->

# Diseño y Estructura (20%)

**Qué se evalúa:**
* Descomposición en funciones
* Evita repetición (DRY)
* Lógica clara
* Organización apropiada

**Niveles:**
* **Excelente:** Modular, elegante
* **Bueno:** Bien estructurado
* **Suficiente:** Estructura básica
* **Insuficiente:** Monolítico, repetitivo

<!--
NOTAS DEL ORADOR:
- ¿Convertiste el problema en piezas manejables?
- ¿O es una sola función `main` de 500 líneas?
-->

---

<!-- _header: 'Dimensión 4' -->

# Apropiación de Herramientas (10%)

**Qué se evalúa:**
* Uso de estructuras apropiadas
* Aprovecha funcionalidades Python
* No reinventa la rueda
* Usa bibliotecas cuando corresponde

**Niveles:**
* **Excelente:** Uso experto de herramientas
* **Bueno:** Uso apropiado
* **Suficiente:** Uso básico
* **Insuficiente:** No usa herramientas

<!--
NOTAS DEL ORADOR:
- Si Python tiene una función `max()`, no escribas un lazo manual de 10 líneas para buscar el máximo (a menos que el ejercicio lo pida explícitamente).
-->

---

<!-- _header: 'Ejemplo Nivel 10' -->

# Código excelente (100 puntos)

```python
def calcular_promedio(numeros):
    """
    Calcula promedio de lista de números.
    
    Args:
        numeros: Lista de números
        
    Returns:
        float: Promedio o None si lista vacía
    """
    if not numeros:
        return None
    
    if not all(isinstance(n, (int, float)) for n in numeros):
        raise TypeError("Todos deben ser números")
    
    return sum(numeros) / len(numeros)


# Tests
try:
    assert calcular_promedio([1, 2, 3]) == 2.0
    assert calcular_promedio([]) is None
    print("✅ Tests pasados")
except AssertionError:
    print("❌ Tests fallaron")
```

<!--
NOTAS DEL ORADOR:
- Notar: Docstring, validación, uso de built-ins (`sum`, `len`, `all`), tests con `assert`.
-->

---

<!-- _header: 'Ejemplo Nivel 7' -->

# Código satisfactorio (70 puntos)

```python
def calcular_promedio(numeros):
    """Calcula promedio."""
    if len(numeros) == 0:
        return 0
    
    suma = 0
    for num in numeros:
        suma = suma + num
    
    promedio = suma / len(numeros)
    return promedio

# Probar
lista = [1, 2, 3]
resultado = calcular_promedio(lista)
print(resultado)
```

**Funciona pero:**
* Menos eficiente
* Sin validación
* Retorna 0 en lugar de None

<!--
NOTAS DEL ORADOR:
- Está bien, pero es "básico".
- No considera casos especiales profesionalmente.
-->

---

<!-- _header: 'Ejemplo Nivel 5' -->

# Código insuficiente (50 puntos)

```python
def prom(l):
    s=0
    for i in l:
        s=s+i
    return s/len(l)

# probar
print(prom([1,2,3]))
```

**Problemas:**
* Nombres crípticos
* Sin documentación
* Crash con lista vacía
* Sin espacios (PEP 8)

<!--
NOTAS DEL ORADOR:
- Este código "anda" pero no es aceptable.
- Ilegible para otros.
-->

---

<!-- _header: 'Checklist' -->

# Antes de entregar

**Verifica:**
- [ ] ¿Funciona correctamente?
- [ ] ¿Probaste casos borde?
- [ ] ¿Nombres descriptivos?
- [ ] ¿Sigue PEP 8?
- [ ] ¿Docstrings en funciones?
- [ ] ¿Comentarios útiles?
- [ ] ¿Dividido en funciones?
- [ ] ¿Sin repetición?
- [ ] ¿Usa herramientas apropiadas?
- [ ] ¿Ejecuta sin errores?

<!--
NOTAS DEL ORADOR:
- Autoevaluación. No manden el trabajo sin revisar esto.
-->

---

<!-- _header: 'Errores comunes' -->

# Qué evitar

**❌ Código que no ejecuta:**
* Errores de sintaxis
* Variables no definidas
* Imports faltantes

**❌ Nombres vagos:**
```python
def f(x):  # ¿Qué hace f?
    return x * 2
```

**❌ Sin validación:**
```python
def dividir(a, b):
    return a / b  # Crash si b=0
```

<!--
NOTAS DEL ORADOR:
- Los errores de sintaxis son inaceptables en una entrega final.
-->

---

<!-- _header: 'Errores comunes' -->

# Qué evitar (cont.)

**❌ Código repetitivo:**
```python
suma1 = n1 + n2
suma2 = n3 + n4
suma3 = n5 + n6
# ... usar función
```

**❌ Todo en una función:**
```python
def main():
    # 200 líneas de código
    pass
```

**❌ Sin estructura:**
```python
# Todo el código sin funciones
input()
if...
for...
# 100 líneas más
```

<!--
NOTAS DEL ORADOR:
- "The God Function" (la función que todo lo hace) es un anti-patrón.
-->

---

<!-- _header: 'Mejora continua' -->

# Ciclo de mejora

**1. Escribir:**
* Hacer que funcione

**2. Revisar:**
* ¿Es legible?
* ¿Sigue convenciones?

**3. Refactorizar:**
* Mejorar estructura
* Extraer funciones
* Eliminar repetición

**4. Documentar:**
* Docstrings
* Comentarios útiles

<!--
NOTAS DEL ORADOR:
- El código no nace perfecto. Se pule.
-->

---

<!-- _header: 'Ejemplo refactoring' -->

# Antes y después

**Versión 1 (funciona):**
```python
x = int(input())
y = int(input())
if y == 0:
    print("error")
else:
    print(x/y)
```

**Versión 2 (profesional):**
```python
def dividir_seguro():
    """Divide dos números ingresados por usuario."""
    try:
        dividendo = int(input("Dividendo: "))
        divisor = int(input("Divisor: "))
        resultado = dividendo / divisor
        print(f"Resultado: {resultado:.2f}")
    except ValueError:
        print("Error: Ingresá números válidos")
    except ZeroDivisionError:
        print("Error: No se puede dividir por 0")

dividir_seguro()
```

<!--
NOTAS DEL ORADOR:
- Mostrar el salto de calidad.
-->

---

<!-- _header: 'Tabla de puntajes' -->

# Distribución típica

| Nivel | Puntos | Descripción |
|-------|--------|-------------|
| 10 | 100 | Excelente, profesional |
| 9 | 90 | Muy bueno, pulido |
| 8 | 80 | Bueno, sólido |
| 7 | 70 | Satisfactorio |
| 6 | 60 | Suficiente, básico |
| ≤5 | ≤50 | Insuficiente |

**Objetivo mínimo: Nivel 6 (60%)**

<!--
NOTAS DEL ORADOR:
- El sistema es binario: Aprobado o Desaprobado.
- 6 es el piso.
-->

---

<!-- _header: 'Feedback' -->

# Aprender del feedback

**Al recibir correcciones:**
1. Leer comentarios cuidadosamente
2. Entender qué mejorar
3. Aplicar en siguiente entrega
4. Preguntar si algo no está claro

**Feedback es para aprender:**
* No es personal
* Todos mejoramos iterativamente
* Errores son parte del proceso

<!--
NOTAS DEL ORADOR:
- No se sientan mal si les marcamos muchas cosas. Es para que aprendan.
-->

---

<!-- _header: 'Recursos' -->

# Herramientas de ayuda

**Verificar estilo:**
```bash
pycodestyle mi_codigo.py
flake8 mi_codigo.py
```

**Formatear automáticamente:**
```bash
black mi_codigo.py
```

**Análisis estático:**
```bash
pylint mi_codigo.py
```

**Usar en cada entrega**

<!--
NOTAS DEL ORADOR:
- Usen la tecnología a su favor.
-->

---

<!-- _header: 'Resumen' -->

# Para recordar

**4 Dimensiones:**
1. **Corrección (40%)** - ¿Funciona?
2. **Estilo (30%)** - ¿Es legible?
3. **Diseño (20%)** - ¿Está bien estructurado?
4. **Herramientas (10%)** - ¿Usa lo aprendido?

**Objetivo:**
* Código que funciona
* Y que se entiende
* Y que está bien hecho

**"Código profesional desde el inicio"**

<!--
NOTAS DEL ORADOR:
- Cierre.
-->

---

<!-- _class: centered -->

# ¿Preguntas?