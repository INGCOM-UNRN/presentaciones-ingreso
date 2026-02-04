---
marp: true
theme: UNRN
paginate: false
header: 'UNRN Andina'
footer: 'Curso de Ingreso - Ingeniería en Computación - UNRN Andina'
size: 4:3
---

<!-- _class: lead -->
<!-- _footer: 'Excepciones - Parte 4/4' -->

# <!-- fit --> Buenas Prácticas
## Excepciones profesionales
Curso de Ingreso - Ingeniería en Computación

<!--
NOTAS DEL ORADOR:
- Duración estimada: 3 minutos
- Objetivo: Distinguir entre código que "funciona" y código profesional mantenible.
- Gancho: "¿Saben cuál es el peor error? El que no te dice que ocurrió. Vamos a evitar eso."
-->

---

<!-- _header: 'Regla 1' -->

# Ser específico

**❌ Capturar todo:**
```python
try:
    operacion()
except:  # Captura TODO (incluso KeyboardInterrupt)
    print("Error")
```

**✅ Capturar específico:**
```python
try:
    operacion()
except ValueError:
    print("Error de valor")
except TypeError:
    print("Error de tipo")
```

<!--
NOTAS DEL ORADOR:
- "Bare except" (except desnudo) es el anti-patrón #1.
- Captura `Ctrl+C` (KeyboardInterrupt), haciendo que no puedas parar tu programa.
- Captura `SystemExit`.
- Oculta bugs de sintaxis o nombres de variables (`NameError`).
-->

---

<!-- _header: 'Regla 2' -->

# No silenciar errores

**❌ Ocultar problema:**
```python
try:
    operacion_critica()
except Exception:
    pass  # ¡Silencia el error!
```

**✅ Al menos registrar:**
```python
try:
    operacion_critica()
except Exception as e:
    print(f"Error crítico: {e}")
    # O logging.error(e)
```

<!--
NOTAS DEL ORADOR:
- "Pokemon Exception Handling": Gotta catch 'em all! (y no hacer nada).
- Si capturás una excepción y no hacés nada, estás borrando la evidencia del crimen.
- El debugging se vuelve imposible.
-->

---

<!-- _header: 'Regla 3' -->

# Mensajes descriptivos

**❌ Mensaje genérico:**
```python
raise ValueError("Error")
```

**✅ Mensaje útil:**
```python
raise ValueError(
    f"Edad {edad} debe estar entre 0 y 120"
)
```

**El mensaje debe ayudar a entender**

<!--
NOTAS DEL ORADOR:
- El mensaje de error es la UI para el programador.
- Incluir los valores que causaron el error (ej: qué edad era inválida).
-->

---

<!-- _header: 'Regla 4' -->

# Scope mínimo

**❌ try demasiado amplio:**
```python
try:
    # 50 líneas de código
    # Solo 1 puede fallar
except ValueError:
    print("Error")
```

**✅ try mínimo:**
```python
configurar()
preparar()
try:
    operacion_riesgosa()
except ValueError:
    print("Error")
finalizar()
```

<!--
NOTAS DEL ORADOR:
- Si metés todo en el `try`, podés capturar un `ValueError` que no esperabas de otra parte del código.
- Precisión quirúrgica.
-->

---

<!-- _header: 'Regla 5' -->

# Orden de except

**❌ Genérico primero:**
```python
try:
    operacion()
except Exception:  # Captura todo
    print("Error general")
except ValueError:  # Nunca se ejecuta
    print("Error específico")
```

**✅ Específico primero:**
```python
try:
    operacion()
except ValueError:
    print("Error de valor")
except Exception:
    print("Error general")
```

<!--
NOTAS DEL ORADOR:
- Python evalúa los `except` de arriba a abajo.
- Si ponés el balde grande arriba, el vaso chico de abajo nunca recibe agua.
-->

---

<!-- _header: 'Patrón: Reintentos' -->

# Reintentar operación

```python
def operacion_con_reintentos(max_intentos=3):
    """Reintenta operación si falla."""
    for intento in range(max_intentos):
        try:
            return operacion_riesgosa()
        except ErrorTemporal as e:
            if intento == max_intentos - 1:
                raise  # Último intento, propagar error
            print(f"Intento {intento + 1} falló, reintentando...")
            time.sleep(1)
```

<!--
NOTAS DEL ORADOR:
- Patrón clave en sistemas distribuidos o redes.
- "Retry pattern".
-->

---

<!-- _header: 'Patrón: Valor por defecto' -->

# Default cuando falla

```python
def obtener_configuracion(clave, default=None):
    """Obtiene config o devuelve default."""
    try:
        return config[clave]
    except KeyError:
        return default

# Uso
puerto = obtener_configuracion("puerto", 8080)
host = obtener_configuracion("host", "localhost")
```

<!--
NOTAS DEL ORADOR:
- "Graceful degradation".
- Si falla la configuración, usar valores seguros.
-->

---

<!-- _header: 'Patrón: Validación acumulativa' -->

# Acumular errores

```python
def validar_formulario(datos):
    """Valida y acumula errores."""
    errores = []
    
    if not datos.get("nombre"):
        errores.append("Nombre requerido")
    
    if not datos.get("email"):
        errores.append("Email requerido")
    
    if datos.get("edad", 0) < 18:
        errores.append("Debe ser mayor de edad")
    
    if errores:
        raise ValidationError(errores)
    
    return True
```

<!--
NOTAS DEL ORADOR:
- Mejor experiencia de usuario: Decirle TODO lo que está mal de una vez, no error por error.
-->

---

<!-- _header: 'Logging' -->

# Registrar errores

```python
import logging

logging.basicConfig(level=logging.INFO)

def procesar_archivo(nombre):
    """Procesa archivo con logging."""
    try:
        with open(nombre) as f:
            datos = f.read()
        logging.info(f"Archivo {nombre} procesado")
        return datos
    except FileNotFoundError:
        logging.error(f"Archivo {nombre} no encontrado")
        raise
    except Exception as e:
        logging.exception("Error inesperado")
        raise
```

<!--
NOTAS DEL ORADOR:
- Introducción breve al módulo `logging`.
- Mejor que `print` porque se puede guardar en archivo, filtrar por nivel, etc.
-->

---

<!-- _header: 'Context managers' -->

# with: Manejo automático

```python
# ❌ Manual (propenso a errores)
archivo = open("datos.txt")
try:
    contenido = archivo.read()
finally:
    archivo.close()

# ✅ Con context manager
with open("datos.txt") as archivo:
    contenido = archivo.read()
# Se cierra automáticamente
```

**with maneja cleanup automáticamente**

<!--
NOTAS DEL ORADOR:
- El `with` es azúcar sintáctica para un `try...finally`.
- SIEMPRE usar `with` para archivos.
-->

---

<!-- _header: 'Excepciones en APIs' -->

# Documentar excepciones

```python
def dividir(a, b):
    """
    Divide dos números.
    
    Args:
        a: Dividendo
        b: Divisor
        
    Returns:
        float: Resultado de a/b
        
    Raises:
        ValueError: Si b es 0
        TypeError: Si a o b no son números
    """
    if b == 0:
        raise ValueError("Divisor no puede ser 0")
    if not isinstance(a, (int, float)):
        raise TypeError("a debe ser número")
    if not isinstance(b, (int, float)):
        raise TypeError("b debe ser número")
    return a / b
```

<!--
NOTAS DEL ORADOR:
- Las excepciones son parte de la interfaz (API) de tu función.
- El usuario debe saber qué esperar.
-->

---

<!-- _header: 'Testing con excepciones' -->

# Probar que lance error

```python
import pytest

def test_dividir_por_cero():
    """Verifica que lance ValueError."""
    with pytest.raises(ValueError):
        dividir(10, 0)

def test_tipo_incorrecto():
    """Verifica que lance TypeError."""
    with pytest.raises(TypeError):
        dividir("10", 5)
```

<!--
NOTAS DEL ORADOR:
- Testing negativo: Probar que el código falla como debe fallar cuando debe fallar.
-->

---

<!-- _header: 'Ejemplo completo' -->

# Sistema robusto

```python
class Usuario:
    def __init__(self, nombre, edad):
        self.validar_nombre(nombre)
        self.validar_edad(edad)
        self.nombre = nombre
        self.edad = edad
    
    def validar_nombre(self, nombre):
        if not isinstance(nombre, str):
            raise TypeError("Nombre debe ser string")
        if not nombre or len(nombre) < 2:
            raise ValueError("Nombre muy corto")
    
    def validar_edad(self, edad):
        if not isinstance(edad, int):
            raise TypeError("Edad debe ser entero")
        if edad < 0 or edad > 120:
            raise ValueError(f"Edad {edad} inválida")

# Uso
try:
    usuario = Usuario("Ana", 20)
except (ValueError, TypeError) as e:
    print(f"Error creando usuario: {e}")
```

---

<!-- _header: 'Checklist' -->

# Antes de lanzar a producción

**Verifica:**
- [ ] Excepciones específicas (no bare except)
- [ ] Mensajes descriptivos
- [ ] No silenciar errores importantes
- [ ] Logging de errores críticos
- [ ] Documentar excepciones en docstrings
- [ ] Try-catch en scope mínimo
- [ ] Cleanup con finally o with
- [ ] Tests para casos de error
- [ ] Validar entradas críticas

<!--
NOTAS DEL ORADOR:
- Checklist de calidad para el TP.
-->

---

<!-- _class: inverse -->

# <!-- fit --> ¡Excepciones completas!
## Código robusto y profesional

---

<!-- _header: 'Resumen completo' -->

# Lo que aprendiste

**Conceptos:**
* Qué son excepciones
* Tipos comunes
* Flujo de ejecución

**Técnicas:**
* try-except-else-finally
* raise y re-raise
* Excepciones custom

**Buenas prácticas:**
* Ser específico
* No silenciar
* Logging
* Patrones comunes

---

<!-- _header: 'Habilidades' -->

# Ahora podés

**Crear:**
* Programas robustos
* Validaciones profesionales
* Excepciones custom

**Aplicar:**
* Manejo de errores elegante
* Logging efectivo
* Patrones de reintentos

**Próxima sección:**
* Módulos y organización

---

<!-- _class: centered -->

# ¡Felicitaciones!
## Excepciones completadas

---

<!-- _class: centered -->

# ¿Preguntas?
