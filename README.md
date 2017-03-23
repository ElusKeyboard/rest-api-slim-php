# API REST SLIM PHP

Ejemplo de API REST con MicroFramework Slim PHP.


## INSTALACIÓN:

1- Descargar el proyecto:
```
$ cd path-to-your-projects
$ git clone https://github.com/maurobonfietti/api-rest-slimphp.git
$ composer install
```


2- Crear nueva base de datos MySQL. Por ejemplo: "api-rest-slimphp".


3- Crear la estructura de la base de datos:
```
-- ----------------------------
-- Table structure for users
-- ----------------------------
DROP TABLE IF EXISTS `users`;
CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(100) COLLATE utf8_unicode_ci NOT NULL,
  `email` varchar(255) COLLATE utf8_unicode_ci,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;


--
-- Table structure for `tasks`
--
DROP TABLE IF EXISTS `tasks`;
CREATE TABLE IF NOT EXISTS `tasks` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `task` varchar(200) NOT NULL,
  `status` tinyint(1) NOT NULL DEFAULT '1',
  `created_at` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
```


4- Cargar datos de prueba en la base de datos:
```
INSERT INTO `users` VALUES ('1', 'Juan', 'juanmartin@delpotro.com');
INSERT INTO `users` VALUES ('2', 'Federico', null);
INSERT INTO `users` VALUES ('3', 'Leo', null);
INSERT INTO `users` VALUES ('4', 'Carlos', null);
INSERT INTO `users` VALUES ('5', 'Diego', 'diego@gmail.com');


INSERT INTO `tasks` (`id`, `task`, `status`) VALUES (1, 'Find bugs', 1);
INSERT INTO `tasks` (`id`, `task`, `status`) VALUES (2, 'Review code', 1);
INSERT INTO `tasks` (`id`, `task`, `status`) VALUES (3, 'Fix bugs', 1);
INSERT INTO `tasks` (`id`, `task`, `status`) VALUES (4, 'Refactor Code', 1);
INSERT INTO `tasks` (`id`, `task`, `status`) VALUES (5, 'Push to prod', 0);
```


5- Configurar los datos de acceso a la base de datos.

Archivo: src/settings.php
```
        // Database connection settings
        'db' => [
            'host' => '127.0.0.1',
            'dbname' => 'api-rest-slimphp',
            'user' => 'root',
            'pass' => '',
        ],
```


## INICIAR SERVIDOR:

Se puede iniciar el servidor web integrado de PHP ejecutando:
```
$ composer start
```


### NOTA:

El comando o script "composer start" sería el equivalente a ejecutar:
```
$ php -S 0.0.0.0:8080 -t public public/index.php
```


## TESTS:

Acceder a la ruta del proyecto y ejecutar los tests con phpunit:
```
$ cd api-rest-slimphp/
$ phpunit
PHPUnit 5.7.17 by Sebastian Bergmann and contributors.

......................                                            22 / 22 (100%)

Time: 188 ms, Memory: 4.00MB

OK (22 tests, 96 assertions)

```
