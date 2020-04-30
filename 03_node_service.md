# Paso 3: Servicio Node

## Levantar un Servicio Node

Ahora vamos a usar algunos comandos nuevos para crear un `Dockerfile` para buildear una imagen que permita levantar el servicio que se encuentra en `/resources/03_node_service`.

Comandos nuevos de `Dockerfile`:

- `COPY` -- copies files or directories from source and adds them to the filesystem of the container at destination
- `WORKDIR` -- set working directory
- `EXPOSE` -- expose port
- `CMD` -- set executable for container

Por ejemplo, el siguiente podría ser el formato de un `Dockerfile` muy simple:

```
FROM <IMAGEN_BASE>

WORKDIR <WORKDIR_FOLDER>

COPY <SRC> <DST>

RUN <COMANDO>

RUN <OTRO_COMANDO>

EXPOSE <PUERTO>

CMD <COMANDO PARA INICIAR PROGRAMA>
```

### Ejercicio 2

1. Crear un Dockerfile que corra el servicio node y cumpla las siguientes condiciones:

- Imagen Base: `node:12` de https://hub.docker.com/_/node
- Working Directory: `/app`
- Exponga el puerto definido en la variable de entorno `PORT` donde corre la aplicación.

2. Buildear la imagen con:

```
docker build . -t node-service
```

Y luego verificar que se pudo buildear correctamente con:

```
docker image ls
```

3. Levantar un container usando la imagen buildeada y los siguientes flags:

- `-e <ENV_VAR>=<ENV_VAR_VALUE>`: Para definir una variable de entorno, en este caso será necesario para definir el puerto donde correra internamente la aplicación.

- `-p <HOST_PORT>:<CONTAINER_PORT>`: Para publicar un puerto expuesto al host.

#### Notas

- Para instalar las dependencias especificadas en el [`package.json`](/resources/node_service/package.json) se debe correr:

```
npm i
```

[< Primer Dockerfile](02_first_dockerfile.md) | [ Agregamos una DB>](04_database.md)
