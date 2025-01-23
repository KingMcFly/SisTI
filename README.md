# SISTEMA TI TUNICHE SETUP

## 1. Clonar/Obtener el Proyecto
Clona el repositorio desde tu herramienta de control de versiones (Git, etc.) o descarga la carpeta del proyecto Laravel. 

Entra a la carpeta principal del proyecto donde encontrarás archivos típicos de Laravel como:
- `composer.json`
- `artisan`
- `.env.example`
- Carpetas como `config/`, `app/`, etc.

---

## 2. Instalar Dependencias con Composer

Ejecuta el siguiente comando desde la raíz del proyecto para instalar las dependencias necesarias:

```bash
composer install
```

Esto descargará todas las librerías requeridas definidas en `composer.json`.

---

## 3. Copiar y Configurar el Archivo `.env`

Copia el archivo `.env.example` y renómbralo como `.env`:

```bash
cp .env.example .env
```

En Windows, también puedes copiarlo y renombrarlo manualmente.

Edita el archivo `.env` y actualiza los valores de conexión a la base de datos. Por ejemplo:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=prestamos_db
DB_USERNAME=root
DB_PASSWORD=
```

Genera la clave de aplicación ejecutando:

```bash
php artisan key:generate
```

---

## 4. Crear la Base de Datos (Si No Existe)

Crea una base de datos en tu servidor (por ejemplo, MySQL o MariaDB) con el nombre definido en `.env`, como `prestamos_db`.

Asegúrate de que el usuario configurado tenga permisos adecuados para acceder y modificar la base de datos.

---

## 5. Migrar la Base de Datos

Ejecuta las migraciones para crear las tablas necesarias:

```bash
php artisan migrate
```

Esto leerá los archivos de migración en `database/migrations/` y generará las tablas en la base de datos configurada.

Si necesitas cargar datos de prueba, puedes ejecutar los seeders:

```bash
php artisan db:seed
```

---

## 6. Iniciar el Servidor de Desarrollo

Para ejecutar la aplicación en tu entorno local, utiliza:

```bash
php artisan serve
```

Por defecto, el servidor estará disponible en: [http://127.0.0.1:8000](http://127.0.0.1:8000). Abre esa URL en tu navegador.

En un entorno de producción, utiliza un servidor como Apache o Nginx y apunta al directorio `public/`.

---

## 7. Flujo Final Resumido
1. Clona el repositorio y entra a la carpeta.
2. Instala dependencias con:
   ```bash
   composer install
   ```
3. Configura `.env` y ajusta la base de datos.
4. Genera la clave de aplicación:
   ```bash
   php artisan key:generate
   ```
5. Crea la base de datos en tu motor.
6. Migra las tablas:
   ```bash
   php artisan migrate
   ```
7. Inicia el servidor local:
   ```bash
   php artisan serve
   ```
8. Abre [http://127.0.0.1:8000](http://127.0.0.1:8000) en tu navegador.

---

## Posibles Problemas Comunes

### Error: `SQLSTATE[HY000] [1045] Access denied for user`

Revisa las credenciales configuradas en tu archivo `.env`.

### Error: `SQLSTATE[42S02]: Base table or view not found`

Asegúrate de haber ejecutado las migraciones (`php artisan migrate`).

### Permisos en Windows

En entornos como WAMP o XAMPP, verifica que tengas permisos de lectura/escritura en la carpeta del proyecto.

### Falta de APP_KEY

Si no generas la clave de aplicación (`php artisan key:generate`), Laravel mostrará un error: "No application encryption key has been specified".

---

## Resumen

- **Clona** el repositorio y entra en la carpeta.
- **Instala dependencias** con `composer install`.
- **Configura `.env`** y la base de datos.
- **Migra las tablas** con `php artisan migrate`.
- **Inicia el servidor local** con `php artisan serve`.

¡Listo! Con estos pasos tendrás tu proyecto Laravel listo para usarse. 🎉
