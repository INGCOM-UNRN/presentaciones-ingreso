---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'JupyterLab - Parte 2/2' -->

# <!-- fit --> Workflows
## Trabajo eficiente en JupyterLite
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Transformar el uso básico en un proceso productivo y profesional.
- Gancho: "¿Alguna vez pasaron horas arreglando un error para darse cuenta de que solo tenían que reiniciar el kernel? Hoy aprendemos a trabajar en serio."
- Recordar: usamos JupyterLite en https://ingcom-unrn.github.io/jupyterlite/
-->

---

<!-- _header: 'Workflow típico' -->

# Flujo de trabajo

**1. Exploración inicial:**
* Cargar datos
* Ver primeras filas
* Entender estructura

**2. Limpieza:**
* Corregir errores
* Manejar datos faltantes

**3. Análisis:**
* Calcular estadísticas
* Visualizar

**4. Documentar:**
* Añadir conclusiones
* Exportar resultados

<!--
NOTAS DEL ORADOR:
- El ciclo de vida de un notebook no es lineal, es iterativo.
- Pero la estructura final debe parecer lineal para que sea legible.
-->

---

<!-- _header: 'Desarrollo iterativo' -->

# Iterar rápidamente

**Ventaja de notebooks:**
```python
# Celda 1: Cargar datos (ejecutar 1 vez)
datos = cargar_dataset()

# Celda 2: Probar diferentes análisis
# Modificar y re-ejecutar solo esta celda
resultado = analizar(datos, metodo="opcion1")
print(resultado)
```

**No recargar datos cada vez**
* Más rápido
* Menos errores

<!--
NOTAS DEL ORADOR:
- Esta es la "Killer Feature" de Jupyter.
- Si cargar datos tarda 10 minutos, no querés hacerlo cada vez que cambiás una coma en el gráfico.
-->

---

<!-- _header: 'Debugging' -->

# Depurar en notebooks

**Print debugging:**
```python
def procesar(datos):
    print(f"Entrada: {datos[:5]}")  # Ver primeros
    resultado = transformar(datos)
    print(f"Después: {resultado[:5]}")
    return resultado
```

**Variables intermedias:**
```python
# Dividir en pasos
paso1 = filtrar(datos)
paso2 = transformar(paso1)
paso3 = agregar(paso2)
```

**Ver variables:** `%whos`

<!--
NOTAS DEL ORADOR:
- En scripts tradicionales, usás un debugger.
- En notebooks, usás la inspección de variables vivas.
-->

---

<!-- _header: 'Testing rápido' -->

# Probar funciones

**Verificar en celda separada:**
```python
# Celda 1: Definir función
def calcular_promedio(numeros):
    return sum(numeros) / len(numeros)

# Celda 2: Tests rápidos
assert calcular_promedio([1, 2, 3]) == 2
assert calcular_promedio([10]) == 10
print("✅ Tests pasados")
```

**Fácil de modificar y re-probar**

<!--
NOTAS DEL ORADOR:
- Unit testing informal.
- Permite verificar la lógica antes de aplicarla a millones de datos.
-->

---

<!-- _header: 'Organización' -->

# Dividir en secciones

**Usar títulos Markdown:**
```markdown
# 1. Carga de datos

# 2. Preprocesamiento

# 3. Análisis exploratorio

# 4. Modelado

# 5. Resultados
```

**Colapsar secciones:**
* Click en barra lateral izquierda
* Ver solo lo que importa

<!--
NOTAS DEL ORADOR:
- Usar la tabla de contenidos (ToC) es vital en notebooks largos.
-->

---

<!-- _header: 'Múltiples cuadernos' -->

# Trabajar con varios notebooks

**Abrir múltiples archivos:**
* File → Open desde File Browser
* Doble-click en cada `.ipynb`
* Cada notebook abre en pestaña separada

**Cambiar entre pestañas:**
* Click en pestaña
* `Ctrl + Shift + [` / `]` → navegar pestañas
* Arrastrar para reordenar

<!--
NOTAS DEL ORADOR:
- JupyterLab permite tener múltiples notebooks abiertos simultáneamente.
- Útil para comparar código, copiar funciones entre proyectos, o tener referencia y trabajo separados.
-->

---

<!-- _header: 'Vistas paralelas' -->

# Organizar en paneles

**Dividir la vista:**
* Arrastrar pestaña al borde → crea panel
* Arrastrar a borde derecho → vista lado a lado
* Arrastrar a borde inferior → vista apilada

**Configuraciones útiles:**
* Notebook + Terminal
* Notebook + Documentación
* Dos notebooks comparando

**Ajustar tamaño:**
* Arrastrar el divisor entre paneles

<!--
NOTAS DEL ORADOR:
- Arrastrar las pestañas es la clave: al soltar cerca del borde se crean paneles nuevos.
- Muy útil para tener datos en un lado y análisis en otro.
-->

---

<!-- _header: 'Vistas del mismo archivo' -->

# Vista espejo de un notebook

**Crear vista paralela del mismo archivo:**
* Click derecho en pestaña → "New View for Notebook"
* O arrastrar la pestaña manteniendo `Alt`

**Ventajas:**
* Ver celda de definición mientras usás la función
* Comparar secciones distantes del mismo notebook
* Editar en un panel, ver resultado en otro

**Sincronización:**
* Cambios se reflejan en ambas vistas
* Mismo kernel compartido

<!--
NOTAS DEL ORADOR:
- "New View for Notebook" es una función muy potente y poco conocida.
- Ideal para notebooks largos donde necesitás ver dos partes a la vez.
-->

---

<!-- _header: 'Reutilizar código' -->

# Copiar código entre notebooks

**En JupyterLite:**
* No hay archivos `.py` externos
* Copiar funciones entre notebooks

**Buena práctica:**
```python
# Celda de "utilidades" al inicio
def es_primo(n):
    """Verifica si n es primo."""
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# Usar en otras celdas
print(es_primo(17))
```

<!--
NOTAS DEL ORADOR:
- En JupyterLite no podemos importar archivos .py externos fácilmente.
- La solución es tener una celda de "funciones útiles" al inicio.
- Para proyectos más grandes, usar JupyterLab instalado localmente.
-->

---

<!-- _header: 'Configuración inicial' -->

# Celda de setup

**Primera celda estándar:**
```python
# Imports disponibles en JupyterLite
import math
import random
import json

# Para gráficos (si está disponible)
# import matplotlib.pyplot as plt

# Configuración
print("✅ Setup completo")
```

**Nota JupyterLite:**
* Algunas librerías no están disponibles
* Las básicas de Python sí funcionan

<!--
NOTAS DEL ORADOR:
- En JupyterLite algunas librerías como numpy/pandas pueden no estar disponibles o requerir instalación especial.
- Para el curso de ingreso, usamos principalmente Python básico.
- Convención: Todos los imports arriba.
-->

---

<!-- _header: 'Evitar errores comunes' -->

# Buenas prácticas

**❌ Ejecutar celdas fuera de orden:**
```python
# Celda 5
resultado = procesar(datos)

# Celda 3 (ejecutar después)
datos = cargar()  # ❌ Orden incorrecto
```

**✅ Mantener orden lógico:**
* Ejecutar todo desde arriba
* Restart & Run All periódicamente

<!--
NOTAS DEL ORADOR:
- El estado oculto es el enemigo.
- Si el notebook solo funciona si ejecutás la celda 5 antes de la 3, está roto.
-->

---

<!-- _header: 'Estado limpio' -->

# Reiniciar regularmente

**Verificar reproducibilidad:**
1. Kernel → Restart & Clear Output
2. Cell → Run All

**¿Todo funciona?**
* ✅ Código reproducible
* ❌ Dependencias ocultas

**Hacer esto antes de compartir**

<!--
NOTAS DEL ORADOR:
- La prueba de fuego.
- Si falla, arreglar el orden de las celdas.
-->

---

<!-- _header: 'Versionado' -->

# Guardar tu trabajo

**En JupyterLite los archivos están en el navegador**

**Buenas prácticas:**
1. **Descargar frecuentemente**
   * Click derecho → Download
   * Guardar en carpeta del curso

2. **Nombrar con fecha:**
   ```
   ejercicio1_2026-01-30.ipynb
   ```

3. **Subir a Google Drive/OneDrive**
   * Backup en la nube

**Si borrás caché del navegador, perdés todo**

<!--
NOTAS DEL ORADOR:
- Esto es crítico en JupyterLite.
- Los archivos NO están en tu computadora, están en el navegador.
- Hacer backup regularmente.
- Descargar al final de cada sesión de trabajo.
-->

---

<!-- _header: 'Compartir notebooks' -->

# Compartir tu trabajo

**Descargar y enviar:**
1. Click derecho en notebook → Download
2. Enviar archivo `.ipynb` por email/aula virtual

**Alternativas:**
* Copiar a Google Colab (colab.research.google.com)
* Subir a GitHub (renderiza automáticamente)

**Para el curso:**
* Descargar `.ipynb`
* Subir al aula virtual

<!--
NOTAS DEL ORADOR:
- El método más simple: descargar y subir al aula virtual.
- Google Colab puede abrir archivos .ipynb directamente.
-->

---

<!-- _header: 'NBViewer' -->

# Ver notebooks online

**NBViewer:**
* nbviewer.jupyter.org
* Pegar URL de GitHub
* Renderiza notebook

**GitHub:**
* Renderiza `.ipynb` automáticamente
* Sin necesidad de herramientas extra

**Google Colab:**
* colab.research.google.com
* Ejecutar notebooks en la nube
* Alternativa a JupyterLite

<!--
NOTAS DEL ORADOR:
- Si necesitan más potencia o librerías especiales, Colab es buena opción.
- Para el curso básico, JupyterLite es suficiente.
-->

---

<!-- _header: 'Extensiones útiles' -->

# Limitaciones de JupyterLite

**No disponible en JupyterLite:**
* Extensiones personalizadas
* Algunas librerías (numpy, pandas pueden requerir config especial)
* Acceso al sistema de archivos local
* Terminal

**Sí disponible:**
* Python estándar completo
* Markdown y LaTeX
* Gráficos básicos
* Todo lo necesario para el curso

<!--
NOTAS DEL ORADOR:
- JupyterLite es más limitado que JupyterLab instalado.
- Pero para aprender Python básico es perfecto.
- Si necesitan más, instalar JupyterLab localmente o usar Colab.
-->

---

<!-- _header: 'Atajos productivos' -->

# Atajos avanzados

**Modo comando:**
* `Shift + M` → fusionar celdas
* `Ctrl + Shift + -` → dividir celda
* `00` → reiniciar kernel
* `H` → mostrar todos los atajos

**Modo edición:**
* `Ctrl + ]` → indentar
* `Ctrl + [` → desindentar
* `Ctrl + /` → comentar/descomentar

<!--
NOTAS DEL ORADOR:
- `00` (cero cero) es el atajo secreto para reiniciar rápido.
-->

---

<!-- _header: 'Snippets' -->

# Fragmentos reutilizables

**Crear templates:**
```python
# Template de análisis
"""
# Análisis: [NOMBRE]
Fecha: [FECHA]
Autor: [TU NOMBRE]

## Objetivo
[DESCRIBIR]

## Datos
[FUENTE]
"""
```

**Guardar en archivos `.ipynb` base**

<!--
NOTAS DEL ORADOR:
- Tener un "esqueleto" de notebook ahorra tiempo de configuración.
-->

---

<!-- _header: 'Performance' -->

# Medir y optimizar

**Celda específica:**
```python
%%timeit
# Código a medir
resultado = sum(range(10000))
```

**Función específica:**
```python
%timeit sum(range(10000))
```

**Profile completo:**
```python
%prun funcion_compleja(datos)
```

<!--
NOTAS DEL ORADOR:
- No adivinar qué es lento. Medirlo.
-->

---

<!-- _header: 'Ejemplo workflow completo' -->

# Proyecto de análisis

**1. Setup (celda 1):**
```python
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
```

**2. Cargar (celda 2):**
```python
df = pd.read_csv("datos.csv")
print(f"Filas: {len(df)}")
df.head()
```

---

<!-- _header: 'Ejemplo workflow completo' -->

# Proyecto de análisis (cont.)

**3. Limpiar (celda 3):**
```python
# Eliminar nulos
df = df.dropna()

# Convertir tipos
df['fecha'] = pd.to_datetime(df['fecha'])
```

**4. Analizar (celda 4):**
```python
# Estadísticas
stats = df.describe()

# Visualizar
df['columna'].plot(kind='hist')
plt.title("Distribución")
plt.show()
```

---

<!-- _header: 'Ejemplo workflow completo' -->

# Proyecto de análisis (cont.)

**5. Conclusiones (celda Markdown):**
```markdown
## Resultados

* Se encontraron X patrones
* Variable Y es significativa
* Recomendaciones:
  1. Primera acción
  2. Segunda acción
```

**6. Exportar:**
* File → Export → HTML

---

<!-- _header: 'Tips finales' -->

# Consejos prácticos

**✅ Hacer:**
* Reiniciar kernel frecuentemente
* Documentar con Markdown
* Nombrar notebooks descriptivamente
* Limpiar outputs antes de commit
* Ejecutar todo antes de compartir

**❌ Evitar:**
* Celdas muy largas (>50 líneas)
* Variables globales excesivas
* Ejecutar fuera de orden
* Código sin documentar

<!--
NOTAS DEL ORADOR:
- Resumen de higiene de notebooks.
-->

---

<!-- _header: 'Alternativas' -->

# Si necesitás más potencia

**Google Colab:**
* Online, gratis
* GPU disponible
* Más librerías

**JupyterLab local:**
```bash
pip install jupyterlab
jupyter lab
```
* Control total
* Todas las extensiones

**VSCode:**
* Soporte nativo `.ipynb`
* Integrado con IDE

<!--
NOTAS DEL ORADOR:
- Para el curso, JupyterLite es suficiente.
- Si quieren explorar más, Colab o instalar JupyterLab local.
-->

---

<!-- _class: inverse -->

# <!-- fit --> ¡JupyterLite listo!
## Entorno productivo en el navegador

---

<!-- _header: 'Resumen' -->

# Para recordar

**JupyterLite del curso:**
* `https://ingcom-unrn.github.io/jupyterlite/`
* Sin instalación
* Funciona en cualquier navegador

**Workflow:**
1. Abrir JupyterLite
2. Crear/abrir notebook
3. Escribir y ejecutar código
4. **Descargar notebook al terminar**

**Importante:**
* Los archivos están en el navegador
* Descargar siempre antes de cerrar
* Backup en la nube recomendado

---

<!-- _class: centered -->

# ¿Preguntas?