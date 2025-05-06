# Proceso: Conexión Front-end y Back-end con Docker

Este documento describe paso a paso cómo conectar un front-end y un back-end usando Docker, incluyendo los comandos utilizados y una breve descripción de cada uno.

---

## 1. Copiar el proyecto base

```bash
cp -r task2 task3
```
**Descripción:** Copia todo el contenido de la carpeta `task2` a una nueva carpeta llamada `task3` para trabajar en una nueva versión sin perder el trabajo anterior.

---

## 2. Modificar el Front-end

### a) Editar `index.html`
- Agregar `<h1 id="dynamic-content"></h1>` antes del título principal.
- Agregar el siguiente script antes de `</body>`:

```html
<script>
    // Load dynamic data from the back-end on port 5252
    $(function() {
        $.ajax({
            type: "GET",
            url: "http://localhost:5252/api/hello",
            success: function(data) {
                $('#dynamic-content').text(data);
            }
        });
    });
</script>
```
**Descripción:** Permite que el front-end muestre datos dinámicos que vienen del back-end.

---

## 3. Modificar el Back-end

### a) Crear o editar `api.py` con:

```python
from flask import Flask
from flask_cors import CORS

app = Flask(__name__)
CORS(app)

@app.route('/api/hello')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5252)
```
**Descripción:** Crea una API que responde con "Hello, World!" y permite peticiones desde otros orígenes (CORS).

### b) Editar el Dockerfile del back-end para instalar flask-cors:

```dockerfile
RUN pip3 install flask
RUN pip3 install flask-cors
```
**Descripción:** Asegura que el contenedor tenga todo lo necesario para correr Flask y aceptar peticiones del front-end.

---

## 4. Construir las imágenes Docker

### a) Back-end:
```bash
cd task3/back-end
docker build -t softy-pinko-back-end:task3 .
```
**Descripción:** Construye la imagen Docker del back-end con los cambios realizados.

### b) Front-end:
```bash
cd ../front-end
docker build -t softy-pinko-front-end:task3 .
```
**Descripción:** Construye la imagen Docker del front-end.

---

## 5. Ejecutar los contenedores

### a) Ejecutar el back-end:
```bash
docker run -p 5252:5252 -it --rm --name softy-pinko-back-end-task3 softy-pinko-back-end:task3
```
**Descripción:** Inicia el servidor Flask en el puerto 5252 dentro de un contenedor.

### b) Ejecutar el front-end (en otra terminal):
```bash
docker run -p 9000:9000 -it --rm --name softy-pinko-front-end-task3 softy-pinko-front-end:task3
```
**Descripción:** Inicia el servidor Nginx que sirve el front-end en el puerto 9000.

---

## 6. Verificar la comunicación

- Abre en el navegador:  
  `http://localhost:9000/softy-pinko-front-end/`
- Deberías ver el mensaje **Hello, World!** arriba del título principal.

---

## 7. Solución de problemas

Si algún puerto estaba ocupado, detuvimos los contenedores con:

```bash
docker ps
docker stop <nombre_del_contenedor>
```
**Descripción:** Verifica y detiene contenedores que puedan estar usando los puertos necesarios.

---

¡Listo! Ahora tienes una app web con front-end y back-end comunicándose entre sí usando Docker. 