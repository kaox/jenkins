Docker NGINX + Jenkins + Jenkins Slave
=================================

Docker NGINX + Jenkins + Jenkins Slave

-------

### Levantar contenedores


```
$ docker-compose up -d
```

### Detiene contenedores

```
$ docker-compose stop
```

### Ejecuta contenedores

```
$ docker-compose start
```

### Detiene y elimina contenedores

```
$ docker-compose down
```

### Bluemix

```
# Logearse a Cloud Foundry
$ cf ic login

# inicializar
$ cf ic init

# Tag a nuestra imagen con el registry de bluemix
$ docker tag mi_imagen registry.ng.bluemix.net/mi_imagen

# Pushear la imagen a Bluemix
$ docker push registry.ng.bluemix.net/mi_imagen

# Ver imagen subida
$ cf ic ps -a

# Ejecutar container
$ cf ic run --name nombre-contenedor registry.ng.bluemix.net/mi_imagen

# Generar IP publica
$ cf ic ip request

# Asignar IP publica
$ cf ic ip bind IP nombre-contenedor

```
