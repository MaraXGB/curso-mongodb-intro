## Connect to container

```sh
docker-compose exec mongodb bash

```

## Connect with mongosh

```sh
# Local docker
mongosh "mongodb://root:root123@localhost:27017/?tls=false"
# or
# Servidor
mongosh "mongodb+srv://nexdevus:nexdevus123@mongodb101.krgr8uk.mongodb.net/"

```
```sh
show dbs
show collections

```
```sh
use ("platzi_store")
db.products.find()

```

## Disconnect
```sh
.exit

```