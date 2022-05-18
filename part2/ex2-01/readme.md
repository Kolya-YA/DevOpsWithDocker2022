# Exercise 2.1

__!!!__  
The local file _text.log_ must be created before the container starting.  
__!!!__

The solution in the __docker-compose.yml__

```yml
version: "3.9"

services:
    sws-logger:
        image: devopsdockeruh/simple-web-service
        volumes: 
            - ./text.log:/usr/src/app/text.log
        container_name: sws-logger
```
