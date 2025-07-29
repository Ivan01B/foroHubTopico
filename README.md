# foroHubTopico
 Permite registrar usuarios, crear cursos y gestionar tópicos de discusión (temas) relacionados con los cursos. La autenticación está implementada mediante tokens JWT, garantizando seguridad en el acceso a los recursos protegidos. Además, utiliza MySQL como base de datos relacional y Flyway para el control de versiones de las migraciones.


# ForoHub - Proyecto Java Spring Boot

Este es un proyecto académico de backend desarrollado con **Java**, **Spring Boot**, **JWT**, **MySQL** y **Flyway**. Simula el funcionamiento de un foro donde los usuarios pueden crear y gestionar tópicos relacionados con cursos.

---

## ✅ Requisitos

- Java 17 o superior
- MySQL 8+
- Maven
- IDE (IntelliJ, VSCode, etc.)

---

## ⚙️ Configuración

### 1.Descarga el repositorio y descomprime.

Quedara la carpeta ForoHub - descomprime y abre con tu IDE de preferencia.

Inicia MySQL
Importa el archivo foroHub.sql Y selecciona la Base.

Ahora en el proyecto,
📄 Configura application.properties
Ubicado en src/main/resources/application.properties, ajusta con tus datos:

properties
spring.datasource.url=jdbc:mysql://localhost:3306/forohub
spring.datasource.username=tu_usuario
spring.datasource.password=tu_contraseña

▶️ Ejecutar el proyecto

Ejecuta la clase principal del proyecto.

🔐 Autenticación
Realiza un POST a /login con los datos de un usuario registrado.

Puedes agregar un nuevo usuario en la base de datos, agregando el hash de la contraseña.

INSERT INTO usuario (nombre, correoElectronico, contrasena)
VALUES ('usuario', 'usuario@gmail.com', '$2a$10$N8Yw.40gTUrMjds7WVwt1eJCZqzehxW../AE2y9d.q4gK3wX1cZia');

El hash lo puedes sacar ejecutando la clase java "prueba" que se encuentra dentro del proyecto, cambias la contraseña y ejecutas. Devolvera el hash en la consola.

Generar TOKEN.

POST http://localhost:8080/login
En Body:
{
  "correoElectronico": "usuario@gmail.com",
  "contrasena": "123456"
}

Recibirás un token JWT.

Usa ese token en los demás endpoints como:
Authorization: Bearer tu_token

📚 Endpoints principales
POST /login → Iniciar sesión

GET /api/cursos → Ver cursos

POST /api/cursos → Crear curso

GET /api/topicos → Ver tópicos

POST /api/topicos → Crear tópico

DELETE /api/topicos/{id} → Eliminar tópico

📌 Notas
Las contraseñas están encriptadas con BCrypt.

Usa Postman para probar los endpoints fácilmente.

Flyway gestiona las migraciones automáticamente al iniciar el proyecto.


