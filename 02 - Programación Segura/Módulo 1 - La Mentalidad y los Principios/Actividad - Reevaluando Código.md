# 📝 Actividad: Re-evaluando Código con Principios de Diseño Seguro

---

> [!check] Objetivo de la Actividad
> Tomar un fragmento de código funcional pero ingenuo y refactorizarlo aplicando los principios de:
> 1.  Mínimo Privilegio
> 2.  Defensa en Profundidad
> 3.  Reducción de la Superficie de Ataque
> 4.  Fallar de Forma Segura

---

### El Código Original: Un Endpoint para Subir Fotos de Perfil

Imaginemos un script de backend que tiene una ruta (`endpoint`) para que un usuario pueda subir su foto de perfil. El script recibe un `user_id` y el archivo de imagen, lo guarda en el servidor y actualiza la ruta en la base de datos.

```python
# app_inseguro.py
from flask import Flask, request, jsonify
import os
import psycopg2 # Conector de Base de Datos

app = Flask(__name__)
# Ruta donde se guardan las imágenes
app.config['UPLOAD_FOLDER'] = '/var/www/uploads'

# ¡PELIGRO! Credenciales de superusuario directamente en el código.
DB_CONN = "dbname='usuarios_db' user='postgres' host='localhost' password='password123'"

@app.route('/upload_pic', methods=['POST'])
def upload_user_picture():
    # Se confía ciegamente en los datos del formulario
    user_id = request.form['user_id']
    file = request.files['picture']

    try:
        # ¡PELIGRO! Se usa el nombre de archivo original del cliente.
        # Esto es vulnerable a Path Traversal (ej: "../../etc/passwd.jpg")
        filename = file.filename
        file.save(os.path.join(app.config['UPLOAD_FOLDER'], filename))

        # Actualización en la Base de Datos
        conn = psycopg2.connect(DB_CONN)
        cursor = conn.cursor()
        cursor.execute("UPDATE users SET pic_path = %s WHERE id = %s", (filename, user_id))
        conn.commit()
        cursor.close()
        conn.close()

        return jsonify({"message": "Foto subida con éxito!"}), 200
    except Exception as e:
        # ¡PELIGRO! Falla de forma insegura, revelando detalles internos del error.
        return jsonify({"error": f"Ocurrió un error inesperado: {str(e)}"}), 500

if __name__ == '__main__':
    # ¡PELIGRO! El modo debug nunca debe usarse en producción.
    app.run(debug=True)


> Conclusión de la Actividad  
> El código original y el seguro cumplen la misma función, pero su resistencia a ataques es drásticamente diferente. El segundo código es más largo y complejo, pero esa complejidad adicional es el **coste de construir seguridad desde el diseño**. Cada línea añadida tiene un propósito defensivo, creando un sistema robusto y resiliente.
