# SisTI
 Sistema TI Tuniche


1. Clonar/Obtener el proyecto
Clonar el repositorio desde tu herramienta de control de versiones (Git, etc.) o descargar la carpeta del proyecto Laravel.
Sitúate en la carpeta principal del proyecto. Allí verás los archivos típicos de Laravel: composer.json, artisan, .env.example, config/, app/, etc.
2. Instalar dependencias con Composer
En la carpeta raíz del proyecto, abre tu terminal y ejecuta:

bash
Copiar
composer install
Esto descargará e instalará todas las librerías requeridas (indicadas en composer.json).
3. Copiar y configurar el archivo .env
Si existe un archivo .env.example, cópialo o renómbralo a .env.

bash
Copiar
cp .env.example .env
(En Windows, puedes simplemente copiar y renombrar manualmente.)

Abre tu archivo .env en un editor de texto y actualiza los valores de conexión a base de datos, por ejemplo:

env
Copiar
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=prestamos_db
DB_USERNAME=root
DB_PASSWORD=
Ajusta los valores según tu servidor MySQL/MariaDB (o el motor que uses).

Generar la clave de aplicación (APP_KEY) con:

bash
Copiar
php artisan key:generate
4. Crear la base de datos (si no existe)
En tu servidor de base de datos (MySQL, PostgreSQL, etc.), crea una base de datos llamada, por ejemplo, prestamos_db.
Asegúrate de que el usuario (root o cualquiera) tenga los permisos adecuados.
5. Migrar la base de datos
Para crear todas las tablas necesarias (personals, catalogos, prestamos, devoluciones, etc.), ejecuta:

bash
Copiar
php artisan migrate
Esto leerá tus archivos de migración en database/migrations/ y creará las tablas en la base de datos que configuraste en .env.

Si necesitas cargar datos de prueba, puedes usar seeders (por ejemplo, php artisan db:seed), siempre y cuando tengas configurados tus seeders.

6. Iniciar el servidor de desarrollo
Para ver el proyecto en acción, ejecuta:

bash
Copiar
php artisan serve
Por defecto, se abrirá en http://127.0.0.1:8000. Copia y pega esa URL en tu navegador. Deberías ver tu pantalla de bienvenida de Laravel o la página principal de tu aplicación.

Si estás en un entorno de producción, en lugar de php artisan serve usarás Apache / Nginx configurado para apuntar al directorio public/.

7. Flujo final
Instala (composer install).
Crea .env y ajusta la DB.
php artisan key:generate.
Crea la base de datos en tu motor.
php artisan migrate (crea tablas).
php artisan serve (inicia servidor local).
Abre http://127.0.0.1:8000 para ver la aplicación.
Posibles problemas comunes
“SQLSTATE[HY000] [1045] Access denied for user”: Significa que tus credenciales en .env no son correctas para la base de datos.
“SQLSTATE[42S02]: Base table or view not found”: Ocurre si no has ejecutado php artisan migrate o si la migración falló.
Permisos en Windows: Asegúrate de tener acceso de lectura/escritura en la carpeta, especialmente al usar WAMP/XAMPP.
Falta APP_KEY: Si no generaste la clave de app con key:generate, Laravel puede mostrar un error “No application encryption key has been specified”.
