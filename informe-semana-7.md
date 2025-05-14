# Práctica: Contenerización de aplicación React y backend simulado con Docker

## 1. Título  
**Contenerización de aplicación React con Docker y ejecución conjunta con backend simulado**

## 2. Tiempo de duración  
**90 minutos**

## 3. Fundamentos  

En esta práctica se aprenderá a contenerizar una aplicación frontend desarrollada con React utilizando Docker. Para el correcto funcionamiento del sistema, también se ejecutará un servicio backend simulado, el cual será necesario tener en funcionamiento para validar las peticiones desde el frontend.

Se demostrará cómo definir un `Dockerfile` para React, construir la imagen, crear un contenedor y ejecutar el backend por separado. Esto permite familiarizarse con la construcción de imágenes personalizadas, la ejecución de contenedores, y la interacción entre servicios en diferentes puertos.

## 4. Conocimientos previos

- Fundamentos de Docker.
- Conocimientos básicos de React.
- Conocimiento general sobre REST APIs.
- Manejo básico de la terminal y uso de `npm`.

## 5. Objetivos a alcanzar

- Clonar y verificar el correcto funcionamiento de un proyecto React.
- Crear un `Dockerfile` funcional para contenerizar el proyecto.
- Construir la imagen Docker y ejecutar el contenedor.
- Ejecutar un backend simulado de forma local para permitir la interacción con la aplicación React.

## 6. Equipo necesario

- Docker instalado.
- Node.js y npm instalados.
- Conexión a internet.
- Navegador web.

## 7. Material de apoyo

- Docker Docs: https://docs.docker.com/
- React Docs: https://reactjs.org/docs/getting-started.html
- Node.js Docs: https://nodejs.org/en/docs/
- Repositorios:
  - Frontend: https://github.com/Daviddotcoms/suda-frontend-s6
  - Backend simulado: https://github.com/Daviddotcoms/mockAPI

---

## 8. Procedimiento

### Paso 1: Clonar los repositorios

```bash
git clone https://github.com/Daviddotcoms/suda-frontend-s6.git
cd suda-frontend-s6
```
## Paso 2: Verificar funcionamiento del proyecto local

```bash
npm install
npm start
```
## Paso 3: Crear el archivo Dockerfile

A continuación se muestra el contenido del archivo `Dockerfile`:

```Dockerfile
# Imagen base
FROM node:18-alpine

# Directorio de trabajo
WORKDIR /app

# Copiar archivos
COPY . .

# Instalar dependencias
RUN npm install

# Construcción del proyecto
RUN npm run build

# Exponer puerto
EXPOSE 3000

# Comando por defecto
CMD ["npm", "start"]
```
## Paso 4: Construir la imagen Docker

Ejecuta el siguiente comando en la terminal para construir la imagen Docker con el nombre `suda-frontend`:

```bash
docker build -t suda-frontend .
```
## Paso 5: Ejecutar el contenedor

Para ejecutar el contenedor y mapear el puerto 3000 del host al contenedor, utiliza el siguiente comando:

```bash
docker run -p 3000:3000 suda-frontend
```
## Paso 6: Clonar y ejecutar el backend simulado

En una terminal diferente:

```bash
git clone https://github.com/Daviddotcoms/mockAPI.git
cd mockAPI
npm install
npm start
# Esto iniciará el backend en http://localhost:5000.
```
## 9. Resultados esperados

- La imagen `suda-frontend` debe construirse sin errores.
- El contenedor debe ejecutar el frontend en [http://localhost:3000](http://localhost:3000).
- El backend simulado debe responder en [http://localhost:5000](http://localhost:5000).
- La aplicación React debe interactuar correctamente con el backend.

---

## 10. Bibliografía

- [Docker Docs](https://docs.docker.com/)
- [React Official Docs](https://reactjs.org/)
- [Node.js Docs](https://nodejs.org/)
- [GitHub - suda-frontend-s6](https://github.com/tu-usuario/suda-frontend-s6) 
- [GitHub - mockAPI](https://github.com/Daviddotcoms/mockAPI)

---

## 11. Enlace del audio





