# Exercise 2.4

## Add redis to example backend

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
    frontend:
        build: ../../part1/ex1-12
        ports:
            - 5000:5000
```
