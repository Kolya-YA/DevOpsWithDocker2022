# Exercise 2.6

The solution in the __docer-compose.yml__

```yml
version: "3.9"

services:
  myredis:
    image: redis
    restart: unless-stopped
    command: redis-server
  backend:
    build: ../../part1/ex1-13
    ports:
      - 8080:8080
    environment:
      - REDIS_HOST=myredis
      - POSTGRES_HOST=db
      - POSTGRES_PASSWORD=testpsw
    depends_on:
      - db
  frontend:
    build: ../../part1/ex1-12
    ports:
      - 5000:5000
  db:
    image: postgres:13-alpine
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: testpsw
    container_name: testdb
    volumes:
      - database:/var/lib/postgresql/data
volumes:
  database:

```
