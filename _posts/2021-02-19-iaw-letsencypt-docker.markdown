---
layout: post
title:  "Práctica: HTTPS con Let’s Encrypt, Docker y Docker Compose"
date:   2021-02-19 04:40:45 -0600
categories: IAW
---
#  Práctica: HTTPS con Let’s Encrypt, Docker y Docker Compose
En esta práctica vamos a habilitar el protocolo HTTPS en un sitio web PrestaShop que se estará ejecutando sobre contenedores Docker en una instancia EC2 de Amazon Web Services (AWS).

Lo primero que haremos será crearnos una nueva instancia en Amazon Web Services.

Registraos un nombre de dominio por ejemplo en [Freenom](https://freenom.com)

Configuramos los DNS en Freenom
![DNS](images/2021-02-19-iaw-letsencypt-docker/dns.PNG)

Realizamos la instalacion de Docker y Docker-Compose
```
apt install docker
```
```
apt install docker-compose
```
Modificamos el archivo [docker-compose](docker-compose.yml) de anteriores prácticas añadiendo la configuración para HTTPS-PORTAL.

Desplegamos los servicios de Docker-Compose y realizamos la instalación de Prestashop
![DNS](images/2021-02-19-iaw-letsencypt-docker/instalacion.PNG)
Cuando hayamos instalado nuestra aplicación web (en este caso Prestashop) cabe la posibilidad de que tengamos que activar el protocolo SSL desde el panel de administración, si no nos deja, podemos hacerlo modificando la base de datos. Vamos al PhpMyAdmin y ejecutamos las siguientes instrucciones en el apartado SQL o modificando los valores de forma gráfica.
```
UPDATE ps_configuration SET value=1 WHERE name="PS_SSL_ENABLED";

UPDATE ps_configuration SET value=1 WHERE name="PS_SSL_ENABLED_EVERYWHERE";
```
Con estos cambios hechos si entramos a nuestro sitio web Prestashop podremos observar que ya es un sitio completamente seguro.

![DNS](images/2021-02-19-iaw-letsencypt-docker/prestashop.PNG)
