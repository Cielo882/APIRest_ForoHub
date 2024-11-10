# ForoHub

ForoHub es una aplicación backend de consola desarrollada con Spring Boot, que permite gestionar un foro de discusión con funcionalidades CRUD, autenticación y autorización usando JWT y Spring Security.

## Requisitos previos

- **Java**: JDK 17 o superior
- **Spring Boot**: versión 3.3.5
- **SQL Server**: como base de datos
- **Spring Tools IDE**: para desarrollo y ejecución
- **Configuración en `application.properties`**: archivo de configuración para conexión a la base de datos, secret key de JWT y otros parámetros de autenticación.

## Instalación

1. **Clona el repositorio**:
   ```bash
   git clone <URL-del-repositorio>
   cd ForoHub
Configura la base de datos en application.properties:

properties:

spring.datasource.url=jdbc:sqlserver://localhost:1433;databaseName=ForoHub
spring.datasource.username=<tu-usuario>
spring.datasource.password=<tu-contraseña>

JWT Secret Key: Define jwt.secret en application.properties: 

jwt.secret=tu_llave_secreta_personalizada
jwt.expiration=3600000
Carga de datos inicial: La base de datos puede poblarse con datos iniciales mediante el archivo import.sql, ubicado en la carpeta src/main/resources.


**Endpoints**
Autenticación y Autorización (Integración con Spring Security y JWT)
ForoHub protege sus endpoints mediante autenticación JWT y autorización a través de Spring Security. La autenticación se realiza mediante el endpoint /login, el cual devuelve un token JWT que debe incluirse en cada petición para autorizar el acceso a las diferentes funcionalidades de la API.

/login (POST): Autenticación de usuario mediante JWT.
Request: JSON con username y password.
Response: Token JWT para el acceso a otros endpoints.
Autorización: Este token se debe enviar en el encabezado de cada solicitud como Authorization: Bearer <token>.
Gestión de Usuarios

/usuarios (POST): Crear un nuevo usuario.
/usuarios/{id} (GET): Obtener un usuario específico por ID.
/usuarios/{id} (PUT): Actualizar información de un usuario.
/usuarios/{id} (DELETE): Eliminar un usuario específico.
Gestión de Publicaciones

/publicaciones (GET): Listar todas las publicaciones.
/publicaciones (POST): Crear una nueva publicación.
/publicaciones/{id} (GET): Obtener detalles de una publicación específica.
/publicaciones/{id} (PUT): Actualizar una publicación.
/publicaciones/{id} (DELETE): Eliminar una publicación.
Comentarios

/publicaciones/{id}/comentarios (POST): Agregar un comentario a una publicación.
/publicaciones/{id}/comentarios/{comentarioId} (DELETE): Eliminar un comentario de una publicación.

**Seguridad y Autorización**
ForoHub emplea Spring Security para la gestión de seguridad y JWT para la autenticación, permitiendo el acceso seguro a los endpoints. Para probar los endpoints:

Genera el token usando el endpoint /login.
Incluye el token en el encabezado Authorization en las solicitudes a los endpoints seguros, usando el formato:

Authorization: Bearer <token>

Futuras Mejoras
Interfaz Web: Integrar una capa frontend para acceso vía navegador.
