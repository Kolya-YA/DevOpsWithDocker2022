# Exercise 2.3

The solution in the __docer-compose.yml__

```yml
version: "3.9"

services:
    frontend:
        container_name: frontend
        build: ../../part1/ex1-12
        ports:
            - 5000:5000
    backend:
        container_name: backtend
        build: ../../part1/ex1-13
        ports:
            - 8080:8080
```
