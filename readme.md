# MySQL Docker


Konten `docker-compose.yml`
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
    security_opt:
      - seccomp:unconfined
```

Run container:
```terminal
$ docker-compose up
```

Konek mysql docker via command line:
```terminal
$ mysql --host 127.0.0.1 --protocol=tcp -u root -p
```

# Troubleshoot

Jika terjadi error seperti ini di `Sequel Pro`:

```terminal
Authentication plugin 'caching_sha2_password' cannot be loaded: dlopen(/usr/local/mysql/lib/plugin/caching_sha2_password.so, 2): image not found
```

Solusinya masuk via terminal. Jalankan:
```mysql
ALTER USER 'root' IDENTIFIED WITH mysql_native_password BY 'root';
```
