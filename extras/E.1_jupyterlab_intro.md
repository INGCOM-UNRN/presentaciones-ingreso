---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'JupyterLab - Parte 1/2' -->

# <!-- fit --> JupyterLite
## Entorno interactivo en el navegador
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Familiarizarse con la herramienta de trabajo del curso.
- Gancho: "¿Y si les dijera que pueden escribir código, ver los resultados, tomar notas y hacer gráficos, todo en el mismo lugar y SIN instalar nada?"
- JupyterLite es una versión de JupyterLab que corre completamente en el navegador.
-->

---

<!-- _header: '¿Qué es JupyterLab?' -->

# JupyterLite

**Entorno de desarrollo interactivo en el navegador:**
* Notebooks con código + texto + gráficos
* Ejecutar código por celdas
* Ideal para aprendizaje y exploración
* **Sin instalación** - funciona en cualquier navegador

**Combina código, documentación y resultados**

<!--
NOTAS DEL ORADOR:
- "Notebook" como cuaderno de laboratorio de un científico.
- JupyterLite es JupyterLab pero corre 100% en el navegador, sin servidor.
- Ventaja: no hay que instalar Python ni nada.
-->

---

<!-- _header: 'Acceso' -->

# Acceder a JupyterLite

**URL del curso:**
```
https://ingcom-unrn.github.io/jupyterlite/
```

**Pasos:**
1. Abrir el enlace en el navegador
2. Esperar que cargue (primera vez tarda un poco)
3. ¡Listo para usar!

**No requiere:**
* Instalación de Python
* Cuenta de usuario
* Conexión permanente (funciona offline después de cargar)

<!--
NOTAS DEL ORADOR:
- Mostrar cómo acceder en vivo.
- La primera carga puede tardar porque descarga el kernel de Python al navegador.
- Una vez cargado, funciona incluso sin internet.
-->

---

<!-- _header: 'Interfaz' -->

# Componentes principales

**Panel izquierdo:**
* Explorador de archivos
* Notebooks abiertos
* Índice del documento

**Área central:**
* Notebooks y archivos
* Pestañas múltiples

**Panel derecho (opcional):**
* Inspector de variables
* Ayuda contextual

<!--
NOTAS DEL ORADOR:
- La interfaz es idéntica a JupyterLab tradicional.
- Recorrido visual rápido por la interfaz.
- Mencionar la posibilidad de "drag & drop" de celdas.
-->

---

<!-- _header: 'Crear notebook' -->

# Nuevo notebook

**Pasos:**
1. Click en **+** (Launcher)
2. Seleccionar **Python (Pyodide)** en Notebook
3. Se crea archivo `.ipynb`

**O desde menú:**
* File → New → Notebook

<!--
NOTAS DEL ORADOR:
- Explicar la extensión `.ipynb` (IPython Notebook).
- Pyodide es el kernel de Python que corre en el navegador.
- Es Python real, con la mayoría de las librerías estándar.
-->

---

<!-- _header: 'Celdas' -->

# Tipos de celdas

**Code (código):**
```python
# Celda de código Python
x = 10
y = 20
print(x + y)
```

**Markdown (texto):**
```markdown
# Título
## Subtítulo

Este es **texto formateado** con Markdown.
```

**Cambiar tipo:** menú desplegable o atajos

<!--
NOTAS DEL ORADOR:
- La distinción clave: Code se ejecuta en Python, Markdown se renderiza como HTML.
-->

---

<!-- _header: 'Ejecutar celdas' -->

# Ejecutar código

**Ejecutar celda actual:**
* `Shift + Enter` → ejecuta y avanza
* `Ctrl + Enter` → ejecuta y queda en celda
* Botón ▶️ en toolbar

**Ejecutar todo:**
* Run → Run All Cells

**Estado:**
* `In [1]:` → ejecutada
* `In [*]:` → ejecutando
* Sin número → no ejecutada

<!--
NOTAS DEL ORADOR:
- `Shift + Enter` es el atajo más importante que aprenderán hoy.
- Explicar el asterisco `[*]` como indicador de "ocupado".
-->

---

<!-- _header: 'Atajos útiles' -->

# Atajos de teclado

**Modo comando (celda sin editar):**
* `A` → insertar celda arriba
* `B` → insertar celda abajo
* `DD` → eliminar celda
* `M` → cambiar a Markdown
* `Y` → cambiar a Code

**Modo edición (editando celda):**
* `Esc` → salir a modo comando
* `Tab` → autocompletar
* `Shift + Tab` → ayuda rápida

<!--
NOTAS DEL ORADOR:
- Productividad. No usar el mouse para todo.
- A (Above), B (Below).
-->

---

<!-- _header: 'Markdown en celdas' -->

# Formatear texto

**Títulos:**
```markdown
# Título 1
## Título 2
### Título 3
```

**Énfasis:**
```markdown
**negrita**
*cursiva*
`código en línea`
```

**Listas:**
```markdown
* Item 1
* Item 2
  * Sub-item
```

<!--
NOTAS DEL ORADOR:
- Ya vieron esto en la guía de Markdown, pero repasarlo aquí contextualiza su uso en Jupyter.
-->

---

<!-- _header: 'Markdown avanzado' -->

# Más formateo

**Código:**
````markdown
```python
def saludar():
    print("Hola")
```
````

**LaTeX:**
```markdown
Fórmula en línea: $E=mc^2$

Bloque:
$$
\int_a^b f(x)dx = F(b) - F(a)
$$
```

**Enlaces:**
```markdown
[Texto del enlace](https://ejemplo.com)
```

<!--
NOTAS DEL ORADOR:
- Soporte de LaTeX es excelente para ingeniería y matemáticas.
-->

---

<!-- _header: 'Variables persistentes' -->

# Estado compartido

**Las variables persisten entre celdas:**
```python
# Celda 1
x = 10
y = 20

# Celda 2 (ejecutar después)
print(x + y)  # 30
```

**⚠️ Cuidado con orden de ejecución:**
* Ejecutar celdas fuera de orden puede causar errores
* Reiniciar kernel limpia todo

<!--
NOTAS DEL ORADOR:
- El peligro oculto de los notebooks: El estado oculto.
- Si borrás una celda, la variable que definiste en ella sigue en memoria hasta reiniciar.
-->

---

<!-- _header: 'Kernel' -->

# Administrar el kernel

**Kernel = intérprete Python (Pyodide):**
* Mantiene variables en memoria
* Ejecuta el código en el navegador

**Acciones:**
* **Restart** → limpia todo, empieza de cero
* **Restart & Run All** → limpia y ejecuta todo
* **Interrupt** → detener ejecución

**Menú Kernel o toolbar**

<!--
NOTAS DEL ORADOR:
- En JupyterLite, el kernel es Pyodide (Python compilado a WebAssembly).
- "Apagar y volver a encender" es la solución al 90% de los problemas.
- `Interrupt` si caemos en un lazo infinito.
-->

---

<!-- _header: 'Ayuda rápida' -->

# Obtener ayuda

**Símbolo ?:**
```python
# Ver documentación
print?
len?
list.append?
```

**Shift + Tab:**
* Presionar dentro de paréntesis
* Muestra firma de función
* Presionar 2 veces → más detalle

**?? para ver código fuente:**
```python
mi_funcion??
```

<!--
NOTAS DEL ORADOR:
- No hace falta ir a Google para todo. La documentación vive en el notebook.
-->

---

<!-- _header: 'Autocompletado' -->

# Tab completion

**Autocompletar:**
```python
# Escribir y presionar Tab
import ma<Tab>  # → math

# Métodos de objetos
texto = "hola"
texto.<Tab>  # Muestra todos los métodos
```

**Muy útil para explorar**

<!--
NOTAS DEL ORADOR:
- Excelente para descubrir métodos de objetos desconocidos.
-->

---

<!-- _header: 'Comandos mágicos' -->

# Magic commands

**Comandos especiales con %:**
```python
# Medir tiempo de ejecución
%timeit sum(range(1000))

# Ver variables
%whos

# Ejecutar script externo
%run mi_script.py

# Directorio actual
%pwd

# Listar archivos
%ls
```

<!--
NOTAS DEL ORADOR:
- Magics de línea (`%`) vs Magics de celda (`%%`).
-->

---

<!-- _header: 'Magic commands dobles' -->

# %% para celdas completas

**Comandos con %%:**
```python
%%timeit
# Todo el código de la celda
total = 0
for i in range(1000):
    total += i
```

```python
%%writefile archivo.txt
Este texto se escribe
en el archivo
```

<!--
NOTAS DEL ORADOR:
- `%%writefile` es genial para crear archivos de prueba.
-->

---

<!-- _header: 'Gráficos inline' -->

# Matplotlib en notebooks

**Mostrar gráficos:**
```python
import matplotlib.pyplot as plt

# Datos
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]

# Crear gráfico
plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('x²')
plt.title('Función cuadrática')
plt.show()
```

**Gráfico aparece bajo la celda**

<!--
NOTAS DEL ORADOR:
- Visualización de datos es el punto fuerte de Jupyter.
-->

---

<!-- _header: 'Organización' -->

# Estructura de notebook

**Buena práctica:**
```markdown
# Título del proyecto
Descripción breve

## 1. Importaciones
[celda con imports]

## 2. Configuración
[constantes y parámetros]

## 3. Carga de datos
[código para cargar]

## 4. Análisis
[celdas de análisis]

## 5. Conclusiones
[resumen y resultados]
```

<!--
NOTAS DEL ORADOR:
- Un notebook es una historia. Debe tener narrativa.
-->

---

<!-- _header: 'Guardar y exportar' -->

# Gestión de archivos

**Guardar:**
* `Ctrl + S` o `Cmd + S`
* Los archivos se guardan en el navegador (localStorage)

**Descargar notebook:**
* Click derecho → Download
* Guardar `.ipynb` en tu computadora

**Importante en JupyterLite:**
* Los archivos están en el navegador
* Si borrás caché, se pierden
* **Descargá tus notebooks importantes**

<!--
NOTAS DEL ORADOR:
- Diferencia clave con JupyterLab normal: archivos en el navegador.
- SIEMPRE descargar los trabajos importantes a la computadora.
- Si cambiás de navegador o borrás datos, perdés los archivos.
-->

---

<!-- _header: 'Ejemplo práctico' -->

# Notebook de análisis

**Celda 1 (Markdown):**
```markdown
# Análisis de números primos
Verificar si números son primos
```

**Celda 2 (Code):**
```python
def es_primo(n):
    """Verifica si n es primo."""
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True
```

---

<!-- _header: 'Ejemplo práctico' -->

# Notebook de análisis (cont.)

**Celda 3 (Code):**
```python
# Encontrar primos hasta 50
primos = [n for n in range(2, 51) if es_primo(n)]
print(f"Primos encontrados: {len(primos)}")
print(primos)
```

**Celda 4 (Markdown):**
```markdown
## Resultados
Se encontraron 15 números primos entre 2 y 50.
```

---

<!-- _header: 'Resumen' -->

# Para recordar

**JupyterLite del curso:**
* `https://ingcom-unrn.github.io/jupyterlite/`
* Sin instalación, funciona en navegador
* Celdas de código y Markdown
* Variables persistentes

**Atajos útiles:**
* `Shift + Enter` → ejecutar
* `B` → nueva celda abajo
* `M` / `Y` → cambiar tipo
* `Tab` → autocompletar

**Importante:**
* Descargar notebooks para no perderlos

<!--
NOTAS DEL ORADOR:
- Cierre.
- Recordar la URL del curso.
-->

---

<!-- _class: centered -->

# ¿Preguntas?