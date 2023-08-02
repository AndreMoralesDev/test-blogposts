---
title: 'Blog con comentarios'
date: '2023-07-20'
---

Imaginemos que estás desarrollando una **API REST** para un blog que permite a los usuarios publicar artículos y realizar comentarios en ellos. El ejercicio consiste en implementar las siguientes funcionalidades:

## **Entidades:**
### **Users:**
- id (ID del usuario)
- username (Nombre de usuario)
- password (Contraseña del usuario)
- roles (Roles del usuario)

### **Articles**
- id (ID del artículo)
- title (Título del artículo)
- content (Contenido del artículo)
- author (Autor del artículo)
- publishDate (Fecha de publicación del artículo)
- comments (Comentarios del artículo)

### **Comments**
- id (ID del comentario)
- article (Artículo al que pertenece el comentario)
- user (Usuario que realizó el comentario)
- content (Contenido del comentario)
- commentDate (Fecha del comentario)

## **Operaciones y URLs:**
### **Crear un usuario:**

URL: /users  
Operación: **POST**  
Cuerpo JSON de ejemplo:  
```json
{
  "username": "john_doe",
  "password": "secretpassword"
}
```
Esta operación debe realizar la validación de los campos requeridos y encriptar la contraseña antes de guardarla.
Iniciar sesión (obtener token JWT):

URL: /auth/login  
Operación: **POST**  
Cuerpo JSON de ejemplo:  

```json
{
  "username": "john_doe",
  "password": "secretpassword"
}
```

Esta operación debe autenticar al usuario y devolver un token JWT válido.

### **Crear un artículo:**

URL: /articles  
Operación: **POST**  
Cuerpo JSON de ejemplo:  

```json
{
  "title": "Mi primer artículo",
  "content": "¡Hola mundo! Este es mi primer artículo.",
  "publishDate": "2023-06-10"
}
```

Esta operación debe requerir autenticación mediante el token JWT y asociar el autor del artículo al usuario autenticado.

### **Obtener todos los artículos:**

URL: /articles  
Operación: **GET**  
Esta operación debe devolver una lista de todos los artículos publicados.  

### **Agregar un comentario a un artículo:**

URL: /articles/{articleId}/comments  
Operación: **POST**  
Cuerpo JSON de ejemplo:  

```json
{
  "content": "¡Excelente artículo!"
}
```

Esta operación debe requerir autenticación mediante el token JWT, validar que el artículo exista y asociar el comentario al usuario autenticado y al artículo correspondiente.

### **Obtener todos los comentarios de un artículo:**

URL: /articles/{articleId}/comments  
Operación: **GET**  
Esta operación debe devolver una lista de todos los comentarios del artículo especificado.