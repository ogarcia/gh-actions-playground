# OpenJDK

Para facilitar la construcción de las imágenes de los diferentes módulos que
forman parte de Smart Wifi se ha creado este _Makefile_ en donde simplemente
se tiene que indicar la version actual de [Alpine][1] y la versión de
OpenJDK que se quiera utilizar.

Una vez creada esta imagen y subida al repositorio el resto de imágenes la
utilizarán como base para el despliegue de las diferentes aplicaciones.

[1]: https://alpinelinux.org/

## Contruir la imagen docker

Al pasar la orden `make` o `make all` se construirá la imagen docker y se le
realizará una comprobación simple de que el comando `java` funciona.

## Otros comandos

* `make build`: simplemente construye la imagen sin el test posterior.
* `make test`: realiza el test a la imagen, si no existe dará error.
* `make clean`: borra las imagenes locales existentes, se puede ejecutar con
  la orden `clean-pre` o `clean-pre` para eliminar solo una de ellas.
* `make run`: ejecuta la imagen con un shell de root.
* `make push-pre`: realiza el docker push para enviar la imagen al ACR.
  Nota: se debe haber ejecutado previamente el `make`, `make all` o `make
  build`.
* `make push-pro`: igual que `make push-pre` pero para producción. Tiene la
  misma dependencia.
