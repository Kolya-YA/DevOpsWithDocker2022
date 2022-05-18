# Exercise 2.2

The solution in the __docker-compose.yml__

```yml
version: "3.9"

services:
    sws-server:
        container_name: sws-server
        image: devopsdockeruh/simple-web-service
        ports:
            - 8080:8080
        command: server
```
