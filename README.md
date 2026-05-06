# Autocarga PHP - Demostración de PSR-4 con Composer

![PHP](https://img.shields.io/badge/PHP-8.x-blue)
![Composer](https://img.shields.io/badge/Composer-Latest-green)
![License](https://img.shields.io/badge/License-MIT-green)

## 📌 Introducción

**Autocarga PHP** es un proyecto de demostración que implementa el estándar PSR-4 para la autocarga de clases en PHP utilizando Composer. Este proyecto ilustra cómo organizar el código en namespaces y cómo Composer facilita la carga automática de clases sin necesidad de incluir manualmente cada archivo.

El proyecto consta de clases simples en diferentes namespaces:
- **App\User**: Una clase de usuario básica.
- **Database\Model\ProductModel**: Un modelo de producto para simular interacciones con la base de datos.

Composer genera el autoloader basado en las configuraciones PSR-4, permitiendo que las clases se carguen bajo demanda (Lazy Loading).

## 🎯 Objetivo

- Demostrar la implementación de PSR-4 con Composer.
- Organizar el código en namespaces y carpetas físicas.
- Mostrar la carga automática de clases sin `require` manual.
- Comprender los beneficios de la autocarga en proyectos PHP.

## ⚙️ Requisitos Previos

Para ejecutar este proyecto, necesitas:

| Herramienta | Versión | Descripción |
|-------------|---------|-------------|
| PHP | 8.0+ | Lenguaje de programación |
| Composer | Última | Gestor de dependencias y autoloader |

## 🛠️ Verificación de Instalación

```bash
php -v
composer -V
```

## 🚀 Instalación

**1. Clonar o descargar el proyecto**
```bash
git clone https://github.com/cedg23/Lab-4-Carga-Automtica.git
cd autocarga
```

**2. Instalar dependencias y generar autoloader**
```bash
composer install
# O si ya tienes las dependencias, regenera el autoloader:
composer dump-autoload
```

Esto genera el archivo `vendor/autoload.php` y configura la autocarga según composer.json.

## 📁 Estructura del Proyecto

La estructura de archivos refleja la relación entre namespaces PSR-4 y las carpetas físicas:

```
autocarga/
├── composer.json          # Configuración de Composer con PSR-4
├── prueba.php             # Script de prueba para demostrar la autocarga
├── App/
│   └── User.php           # Clase App\User
├── Database/
│   └── Model/
│       └── ProductModel.php  # Clase Database\Model\ProductModel
└── vendor/
    ├── autoload.php       # Autoloader generado por Composer
    └── composer/          # Archivos internos de Composer
```

### Relación Namespaces y Carpetas

- **Namespace `App\\`** → Carpeta `App/`
  - Ejemplo: `App\User` se encuentra en `App/User.php`

- **Namespace `Database\Model\\`** → Carpeta `Database/Model/`
  - Ejemplo: `Database\Model\ProductModel` se encuentra en `Database/Model/ProductModel.php`

Esto sigue el estándar PSR-4, donde el namespace raíz mapea a la carpeta base, y las subcarpetas corresponden a subnamespaces.

## ▶️ Pruebas de Ejecución

Para verificar que la autocarga funciona correctamente, ejecuta el script `prueba.php`:

```bash
php prueba.php
```

### Código de Prueba

```php
<?php

require 'vendor/autoload.php';

use App\User;
use Database\Model\ProductModel;

$user = new User();
echo $user->getName();
echo "\n";

$product = new ProductModel();
echo $product->getId();
```

### Salida Esperada

```
Dave
123
```

Esto demuestra que:
- Las clases `App\User` y `Database\Model\ProductModel` se cargan automáticamente sin `require` explícito.
- Los métodos `getName()` y `getId()` se ejecutan correctamente.

### Capturas de Pantalla (Simuladas)

Si ejecutas en terminal:
- **Antes de `composer install`**: Error "Class 'App\User' not found".
- **Después de `composer install`**: Salida correcta como arriba.

## 🧠 Conclusiones Técnicas

### 1. Mantenibilidad
La implementación de PSR-4 con Composer facilita agregar nuevas clases sin modificar archivos de configuración globales. Simplemente crea la clase en la carpeta correspondiente al namespace, y Composer la detecta automáticamente al regenerar el autoloader con `composer dump-autoload`. Esto reduce errores y acelera el desarrollo colaborativo.

### 2. Eficiencia de Memoria
El Lazy Loading permite cargar clases solo cuando se necesitan, optimizando el uso de memoria en el servidor. En lugar de incluir todos los archivos PHP al inicio, Composer carga las clases bajo demanda, mejorando el rendimiento en aplicaciones grandes con muchas clases no utilizadas en cada solicitud.

### 3. Estandarización
Seguir PSR-4 asegura consistencia en la estructura del proyecto, facilitando el trabajo colaborativo. Desarrolladores pueden predecir la ubicación de clases basándose en el namespace, reduciendo conflictos y mejorando la legibilidad del código. Además, es compatible con herramientas y frameworks PHP modernos.

## 📚 Referencias y Documentación
- [Documentación de Composer](https://getcomposer.org/doc/)
- [PSR-4 Autoloading Standard](https://www.php-fig.org/psr/psr-4/)
- [Documentación de PHP sobre Namespaces](https://www.php.net/manual/en/language.namespaces.php)

## 📅 Información del Proyecto
- Fecha de desarrollo: Mayo 2026
- Versión: 1.0.0
- Estado: Completo

## 👨‍💻 Información del Desarrollador
Este proyecto ha sido desarrollado por:

- Nombre: Carlos Díaz
- Correo: carlos.diaz10@utp.ac.pa
- Curso: Desarrollo de Software VII
- Instructor: Irina Fong
- Institución: Universidad Tecnológica de Panamá (UTP)
