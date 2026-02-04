---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Documentación - Parte 1/1' -->

# <!-- fit --> Markdown Básico
## Formato de texto en Jupyter
Curso de Ingreso - Ingeniería en Computación

---

<!-- _header: '¿Qué es Markdown?' -->

# Lenguaje de marcado ligero

Markdown te permite escribir texto con formato (negrita, títulos, listas) usando caracteres simples.

**Ventajas:**
* **Simple:** Se escribe como texto plano.
* **Portable:** Funciona en GitHub, Jupyter, WhatsApp, Discord.
* **Limpio:** Separa el contenido del diseño.

**En Jupyter:**
* Seleccioná una celda.
* Presioná `M` para convertirla a Markdown.
* `Shift + Enter` para renderizar (ver resultado).

---

<!-- _header: 'Estructura' -->

# Títulos y Encabezados

Se usan numerales `#`.

**Código:**
```markdown
# Título Principal (H1)
## Sección (H2)
### Subsección (H3)
#### Título pequeño (H4)
```

**Resultado:**
(Se verán con diferentes tamaños de letra)

**Tip:** Usá `##` para separar ejercicios o temas en tu notebook.

---

<!-- _header: 'Énfasis' -->

# Negrita y Cursiva

**Código:**
```markdown
Esto es *cursiva* o _cursiva_.

Esto es **negrita** o __negrita__.

Esto es ***ambos***.
```

**Resultado:**
Esto es *cursiva* o _cursiva_.
Esto es **negrita** o __negrita__.
Esto es ***ambos***.

---

<!-- _header: 'Organización' -->

# Listas

**No ordenadas (viñetas):**
```markdown
- Manzanas
- Bananas
  - Cavendish
  - Platano
* Naranjas (también sirve *)
```

**Ordenadas (números):**
```markdown
1. Abrir archivo
2. Leer datos
3. Cerrar archivo
```

**Tip:** Markdown enumera automáticamente (podés poner `1.` a todo).

---

<!-- _header: 'Código' -->

# Mostrar código

**En línea (backticks):**
La función `print()` muestra texto.

**Bloque de código (triple backtick):**
```python
def hola():
    print("Hola Mundo")
```

**Tip:** Escribí el lenguaje (`python`) después de los primeros backticks para colorear la sintaxis.

---

<!-- _header: 'Referencias' -->

# Enlaces e Imágenes

**Enlaces:**
`[Texto visible](URL)`
```markdown
[Google](https://www.google.com)
```

**Imágenes:**
`![Texto alternativo](URL_imagen)`
```markdown
![Logo Python](https://python.org/logo.png)
```

**Diferencia:** El signo de exclamación `!` al principio.

---

<!-- _header: 'Avanzado' -->

# Citas y Tablas

**Citas:**
```markdown
> "La simplicidad es mejor que la complejidad."
```

**Tablas:**
```markdown
| Nombre | Edad |
|--------|------|
| Ana    | 25   |
| Juan   | 30   |
```

---

<!-- _header: 'Buenas Prácticas' -->

# Documentar Notebooks

1.  **Título principal:** `# Trabajo Práctico X`.
2.  **Datos personales:** Nombre, fecha.
3.  **Enunciados:** Copiá el enunciado del ejercicio antes del código.
4.  **Explicaciones:** Si el código es complejo, explicá la lógica en texto.
5.  **Conclusiones:** Al final, escribí qué significan los resultados.

**Ejemplo:**
```markdown
## Ejercicio 1
Calculamos el promedio de notas.

[Bloque de código Python]

**Resultado:** El promedio es 8.5.
```

---

<!-- _header: 'Resumen' -->

# Cheat Sheet

* `# Título`
* `**Negrita**`
* `- Lista`
* `` `Código` ``
* `[Link](url)`

**¡Probálo ahora en tu Jupyter!**
Creá una celda, apretá `M`, escribí algo y dale a `Shift + Enter`.
