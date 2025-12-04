# 🅿️ Portal de Estacionamiento: Inter Sellos (UIF)

## 📝 Descripción

Aplicación web Full-Stack desarrollada para modernizar y eficientizar la gestión de permisos de estacionamiento en el campus de la **Universidad Interamericana de Fajardo**. El sistema proporciona una plataforma segura y eficiente para que los usuarios (estudiantes y personal) soliciten, consulten, y actualicen sus permisos de estacionamiento, mientras que el equipo de seguridad y administración utiliza herramientas de gestión completas (CRUD).

## 💡 Funcionalidades Principales

El sistema implementa un completo **CRUD (Crear, Leer, Actualizar, Borrar)** a través de APIs desarrolladas en PHP.

### Módulo de Usuario (Front-End)

* **Registro de Usuarios (`Create User.html`):** Formulario extenso para la captura de datos personales, de licencia y de vehículo, enviado a `create_user.php`.
* **Autenticación (`Login.html`):** Acceso seguro mediante validación de credenciales a través de `Login.php`, utilizando `password_verify()` para la verificación de *hashes* de contraseña.
* **Estado de Permisos (`Permit Status.html`):** Consulta dinámica del historial de sellos, mostrando claramente si un permiso está **ACTIVO** o **EXPIRADO** basado en la fecha de expiración (`Permit-Status.js` consume `Permit-Status.php`).
* **Navegación:** Enlaces directos a recursos del campus (`Inter Web`, `Inter Blackboard`).
* **Contacto:** Formulario de contacto con validación básica (`contact-us.js`).

### Módulo Administrativo (Back-End / Manejo de Seguridad)

* **Administración de Permisos (`CrearPermiso.html`):** Panel principal para la gestión de sellos, permitiendo:
    * **Crear/Actualizar:** Asignar o extender un sello de estacionamiento a un usuario (`ActualizarPermiso.php`).
    * **Eliminar:** Eliminar permanentemente un registro de sello de la tabla `permisos_sello` (`BorrarPermiso.php`).
    * **Consulta:** Obtener la lista completa de usuarios y el estado de sus permisos (`ConseguirPermiso.php`).
* **Control de Acceso (`check_login.php`):** Archivo de control que asegura que las páginas administrativas solo sean accesibles si existe una sesión de usuario válida (`$_SESSION['user_id']`).

## 🛠️ Tecnologías Clave

| Categoría | Tecnología | Descripción / Archivos Clave |
| :--- | :--- | :--- |
| **Back-End** | **PHP** | Lógica de negocio, autenticación, y operaciones CRUD. (e.g., `Login.php`, `create_user.php`, `ActualizarPermiso.php`). |
| **Front-End (Lógica)**| **JavaScript (JS)** | Manejo de formularios, validación, e interacción asíncrona (`fetch`) con el Back-End (e.g., `Login.js`, `Create_user.js`, `AdminPermiso.js`). |
| **Front-End (Estructura)**| **HTML5** | Estructura de las 8 páginas principales del portal (e.g., `Index.html`, `Create User.html`, `Manage Permits.html`). |
| **Estilos** | **CSS / Bootstrap** | Diseño *responsive* con estilos customizados. Paleta de colores institucional (Verde, Negro y acentos Amarillos). |
| **Base de Datos** | **Relacional (MySQL/Apache)** | Se requiere una base de datos relacional con soporte para **PDO** para las consultas en PHP. El sistema asume tablas: `login`, `usuarios_completos` y `permisos_sello`. |

## ⚙️ Estructura de la Base de Datos

El sistema interactúa con tres tablas principales, definidas por las consultas en los archivos PHP:

1.  **`login`**: Almacena credenciales de acceso (`username`, `password_hash`).
2.  **`usuarios_completos`**: Almacena todos los datos de registro (nombre, info. vehicular, `student_id`).
3.  **`permisos_sello`**: Almacena el ID de usuario y la `expiracion_sello`.

## 🚀 Requisitos para la Ejecución

* Un servidor de base de datos **MySQL**.


## 💻 Instalación y Ejecución

* El archivo de configuración de conexión a la base de datos (`db.php`) debe estar presente y configurado en el directorio del Back-End.
* La instalación se basa en la colocación de archivos en la estructura de directorios del servidor web:


## 1. Configurar y crear la Base de Datos
    (Se debe crear un script SQL para las tablas login, usuarios_completos y permisos_sello)

## 2. Configurar el archivo de conexión (db.php en Back-End)


* **// Ejemplo de variables de conexión:**
$host = 'localhost';
$db   = 'inter_sellos';
$user = 'root';
$pass = '';

## 3. Colocar los archivos en el servidor web (e.g. directorio 'htdocs' de XAMPP)
   * **La estructura de carpetas debe ser:**
proyecto-fullstack/
* **├── Back-End/      # Lógica PHP/JS**
* **├── Styles/        # Archivos CSS**
* **├── Pages/         # Archivos HTML**
* **└── photos/        # Imágenes**

## 4. Acceder al portal
  1. Abrir el XAMPP y darle start a Apache y MySQL.
2. Abrir el navegador y navegar a la URL de la página de inicio (Index.html).

URL Típica:
http://localhost/proyecto-fullstack/Pages/Index.html
