# Softy Pinko Docker - Task 3

Este proyecto muestra cómo conectar un front-end y un back-end usando Docker.

## ¿Qué incluye?
- **Front-end:** Página web servida con Nginx
- **Back-end:** API en Flask que responde con un mensaje dinámico

## ¿Cómo correr el proyecto?

1. **Construir las imágenes:**
   ```bash
   cd task3/back-end
   docker build -t softy-pinko-back-end:task3 .
   cd ../front-end
   docker build -t softy-pinko-front-end:task3 .
   ```

2. **Ejecutar los contenedores (en dos terminales):**
   - Back-end:
     ```bash
     docker run -p 5252:5252 -it --rm --name softy-pinko-back-end-task3 softy-pinko-back-end:task3
     ```
   - Front-end:
     ```bash
     docker run -p 9000:9000 -it --rm --name softy-pinko-front-end-task3 softy-pinko-front-end:task3
     ```

3. **Ver en el navegador:**
   - Ir a: [http://localhost:9000/softy-pinko-front-end/](http://localhost:9000/softy-pinko-front-end/)
   - Deberías ver el mensaje "Hello, World!" arriba del título principal.

---

¡Listo! Ahora tienes una app web conectando front-end y back-end con Docker. 