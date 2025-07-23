# 🛠️ Actividad Práctica: Escribir Funciones de Validación Robustas

> [!check] Objetivo
> Aplicar el principio de **validación por listas blancas** para crear funciones reutilizables que puedan sanear diferentes tipos de datos antes de que la aplicación los procese.

Usaremos Python para los ejemplos por su claridad, pero los principios son aplicables a cualquier lenguaje.

### Función 1: Validar un Email

El email tiene un formato conocido. Usaremos una expresión regular (regex) para definir ese formato.

```python
import re

def is_valid_email(email):
    """
    Valida si una cadena de texto tiene el formato de un email.
    Este regex es una simplificación común, no cubre el 100% de los casos
    extremos del RFC, pero es robusto para el uso general.
    """
    if not isinstance(email, str) or len(email) > 254:
        return False
    # Regex para formato de email: algo@algo.dominio
    pattern = re.compile(r"^[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$")
    return re.match(pattern, email) is not None

# --- Pruebas ---
print(f"test@example.com: {is_valid_email('test@example.com')}") # True
print(f"email-invalido: {is_valid_email('email-invalido')}")       # False
print(f"<script>: {is_valid_email('<script>')}")                   # False
### Función 2: Validar un Nombre de Archivo

Este es un caso de seguridad crítico para prevenir Path Traversal. Seremos muy estrictos.import re

def is_safe_filename(filename):
    """
    Valida si un nombre de archivo es seguro, permitiendo solo un conjunto
    restringido de caracteres (lista blanca). Previene Path Traversal.
    """
    if not isinstance(filename, str) or not filename:
        return False
    # No permitir caracteres de directorio como / o \
    if "/" in filename or "\\" in filename:
        return False
    # No permitir ".." para evitar subir un nivel en el directorio
    if ".." in filename:
        return False
    
    # Lista blanca: solo permitir letras, números, guión bajo, guión y punto.
    # El ancla ^ asegura que toda la cadena debe coincidir, de principio a fin ($).
    pattern = re.compile(r"^[a-zA-Z0-9_.-]+$")
    return re.match(pattern, filename) is not None

# --- Pruebas ---
print(f"mi_archivo_1.txt: {is_safe_filename('mi_archivo_1.txt')}")     # True
print(f"../../etc/passwd: {is_safe_filename('../../etc/passwd')}") # False
print(f"foto.jpg; rm -rf /: {is_safe_filename('foto.jpg; rm -rf /')}") # False

### Función 3: Validar un Identificador Numérico (ej. ID de usuario)

Los IDs suelen ser números enteros. La validación es muy simple pero muy importante.
def is_valid_id(user_id):
    """
    Valida si un identificador es un número entero positivo.
    """
    # Intentar convertirlo a entero. Si falla, no es un número.
    try:
        id_num = int(user_id)
        # Asegurarse de que sea positivo (lista blanca de rango)
        return id_num > 0
    except (ValueError, TypeError):
        return False

# --- Pruebas ---
print(f"123: {is_valid_id('123')}")                         # True
print(f"0: {is_valid_id('0')}")                             # False
print(f"'123 OR 1=1': {is_valid_id('123 OR 1=1')}")         # False