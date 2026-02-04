---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Módulos - Introducción' -->

# <!-- fit --> Concepto de Módulos
## Biblioteca Estándar e Imports
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Comprender que no hay que reinventar la rueda.
- Gancho: "¿Saben por qué Python es tan popular? Porque viene con 'baterías incluidas'. Hoy vamos a ver qué significa eso."
-->

---

<!-- _header: 'Filosofía Python' -->

# "Baterías Incluidas"

Python viene con una **Biblioteca Estándar** inmensa.
No tenés que escribir todo desde cero.

**Dos tipos de herramientas:**
1. **Built-ins:** Disponibles siempre (`print`, `len`, `str`, `list`).
2. **Módulos:** Disponibles pero requieren importación (`math`, `random`, `os`).

**¿Por qué separar?**
Para no sobrecargar la memoria con cosas que no siempre usás.

<!--
NOTAS DEL ORADOR:
- Analogía:
    - Built-ins = Los bolsillos de tu pantalón (llaves, billetera). Siempre a mano.
    - Módulos = La caja de herramientas en el garaje. Tenés que ir a buscarla (`import`) solo cuando la necesitás.
- Si Python cargara todo al inicio, tardaría mucho en arrancar.
-->

---

<!-- _header: '¿Qué es un módulo?' -->

# Definición

Un **módulo** es simplemente un archivo `.py` que contiene código Python (funciones, clases, variables).

**Objetivos:**
* **Organización:** Agrupar código relacionado.
* **Reutilización:** Usar el mismo código en varios programas.
* **Namespace:** Evitar conflictos de nombres.

<!--
NOTAS DEL ORADOR:
- Namespace (Espacio de nombres): Imaginen que hay dos estudiantes llamados "Juan". Para distinguirlos usamos sus apellidos.
- Los módulos son como apellidos para las funciones. `math.sqrt` es distinta de `cmath.sqrt`.
-->

---

<!-- _header: 'Sintaxis básica' -->

# La sentencia import

Para usar un módulo, primero debés **importarlo**.

```python
import math

# Ahora tenés acceso a todo lo que hay en math
print(math.pi)          # 3.14159...
print(math.sqrt(16))    # 4.0
```

**Nota:** Debés usar el prefijo `math.` para acceder a sus herramientas.

<!--
NOTAS DEL ORADOR:
- El punto `.` es el operador de acceso. Se lee "del módulo math, dame pi".
-->

---

<!-- _header: 'Alias' -->

# Importar con alias (as)

Si el nombre del módulo es muy largo, podés darle un apodo.

```python
import pandas as pd
import numpy as np
import math as m

# Usamos el alias
print(m.pi)
print(m.cos(0))
```

**Convención:** Algunos alias son estándar en la industria (`pd` para pandas, `np` para numpy).

<!--
NOTAS DEL ORADOR:
- Usar alias estándar es buena práctica porque otros programadores entenderán tu código al instante.
- `import math as m` es común en scripts cortos matemáticos.
-->

---

<!-- _header: 'Importar específicos' -->

# from ... import ...

Si solo necesitás una función específica y no querés escribir el prefijo.

```python
from math import sqrt, pi

# Ahora usás los nombres directamente
print(pi)
print(sqrt(25))
```

**Cuidado:** Si tenés una variable llamada `pi` en tu código, esto la sobrescribirá.

<!--
NOTAS DEL ORADOR:
- Ventaja: Código más limpio (`sqrt(25)` vs `math.sqrt(25)`).
- Desventaja: Posible colisión de nombres. ¿De dónde viene `pi`? ¿Del módulo o es una variable mía?
-->

---

<!-- _header: 'Peligro' -->

# El comodín asterisco (*)

```python
from math import *  # ❌ NO RECOMENDADO
```

Importa **todo** lo que hay en el módulo al espacio de nombres actual.

**¿Por qué es malo?**
* No sabés qué nombres se importaron.
* Puede sobrescribir tus variables sin aviso.
* Hace el código difícil de leer.

**Regla:** Sé explícito. `import math` o `from math import sqrt`.

<!--
NOTAS DEL ORADOR:
- El "Star Import" es el villano de la película.
- Imagina importar dos módulos que ambos tienen una función `open()`. ¿Cuál se usa?
- Solo aceptable en sesiones interactivas rápidas, nunca en código de producción.
-->

---

<!-- _header: 'Exploración' -->

# ¿Qué hay adentro?

¿Cómo sabés qué funciones tiene un módulo?

**Función dir():**
```python
import math
print(dir(math))
# ['__doc__', 'acos', 'asin', 'ceil', 'cos', 'pi', ...]
```

**Función help():**
```python
help(math.cos)
# Muestra la documentación de la función cos
```

<!--
NOTAS DEL ORADOR:
- Herramientas de introspección. Muy útiles en la consola interactiva.
- `dir()` lista el directorio de nombres.
- `help()` muestra el docstring (¿recuerdan que vimos docstrings antes?).
-->

---

<!-- _header: 'Ejemplo Integrador' -->

# Un programa modular

```python
import random
import time

print("Generando números...")
time.sleep(1)  # Pausa de 1 segundo

numero = random.randint(1, 10)
print(f"Tu número de la suerte es: {numero}")
```

**Explicación:**
* `import random`: Herramientas de azar.
* `import time`: Herramientas de tiempo.
* Usamos funciones de ambos módulos en el mismo programa.

<!--
NOTAS DEL ORADOR:
- Un programa real suele importar varios módulos.
- Convención PEP 8: Todos los imports van al principio del archivo.
-->

---

<!-- _header: 'Resumen' -->

# Para recordar

* **Módulos:** Archivos con código reutilizable.
* **import modulo:** Trae el módulo (usar con `modulo.funcion`).
* **import modulo as alias:** Renombra para brevedad.
* **from modulo import funcion:** Trae elementos específicos.
* **Evitar from modulo import *:** Mantiene el código limpio.
* **Biblioteca Estándar:** "Baterías incluidas" (math, random, time, os...).

**Próximo:**
* Módulos específicos: Random y Math.

<!--
NOTAS DEL ORADOR:
- Cierre.
-->