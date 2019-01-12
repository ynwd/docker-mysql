

konten `docker-compose.yml`
```docker
version: '2'

services:
  db:
    container_name: "mysql8"
    image: "mysql:8"
    ports:
      - "3306:3306"
    volumes:
      - .mysql/config:/etc/mysql/conf.d:cached
      - .mysql/data:/var/lib/mysql:cached
      - .mysql/init:/docker-entrypoint-initdb.d:cached
    environment:
      MYSQL_ROOT_PASSWORD: root
```

run container
```terminal
$ docker-compose up
```

konek mysql docker via command line
```terminal
$ mysql --host 127.0.0.1 --protocol=tcp -u root -p
```
