<No puedo crear el archivo directamente, pero aquí tienes el contenido listo para copiar y pegar en un `README.txt` o `README.md`.

---

# Autocarga PHP - Proyecto de PSR-4 con Composer

![PHP](https://img.shields.io/badge/PHP-8.x-blue)  
![Composer](https://img.shields.io/badge/Composer-Latest-green)  
![License](https://img.shields.io/badge/License-MIT-green)

## 📌 Introducción

**Autocarga PHP** es una demostración de uso de Composer y PSR-4 para cargar clases automáticamente en PHP.

El proyecto incluye:
- `App\User`
- `Database\Model\ProductModel`

Composer se encarga de cargar las clases bajo demanda.

## 🎯 Objetivo

- Mostrar la configuración de PSR-4 en composer.json
- Usar `composer install` y `composer dump-autoload`
- Probar la carga automática con `prueba.php`

## ⚙️ Requisitos

- PHP 8.0+
- Composer

## 🛠️ Instalación

```bash
git clone <URL_DEL_REPOSITORIO>
cd autocarga
composer install
# o
composer dump-autoload
```

## 📁 Estructura del Proyecto

```
autocarga/
├── composer.json
├── prueba.php
├── App/
│   └── User.php
├── Database/
│   └── Model/
│       └── ProductModel.php
└── vendor/
    ├── autoload.php
    └── composer/
```

## 📌 Relación Namespace ↔ Carpeta

- `App\` → `App/`
- `Database\Model\` → `Database/Model/`

## ▶️ Prueba de Ejecución

Archivo `prueba.php`:

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

Ejecuta:

```bash
php prueba.php
```

Salida esperada:

```
Dave
123
```

## 📝 Conclusiones Técnicas

### 1. Mantenibilidad
Usar PSR-4 permite agregar nuevas clases sin cambiar archivos de configuración global. Solo se crea la clase en la carpeta correspondiente y Composer la carga.

### 2. Eficiencia de memoria
Composer carga clases cuando se necesitan, en lugar de incluir todos los archivos al inicio. Esto mejora el rendimiento en aplicaciones grandes.

### 3. Estandarización
PSR-4 hace que la estructura del código sea clara y uniforme, lo cual facilita el trabajo en equipo y evita confusiones.

## 📌 .gitignore recomendado

```
/vendor/
composer.lock
```

## 📚 Referencias

- https://getcomposer.org/doc/
- https://www.php-fig.org/psr/psr-4/
- https://www.php.net/manual/es/language.namespaces.php

---
