# Exercise 2.8

The solution in the __docker-compose.yml__

```yml
version: "3"

services:
  backend:
    build: ../../part1/ex1-13

  frontend:
    build: ../../part1/ex1-12

  nginx:
    image: nginx:1.19-alpine
    restart: unless-stopped
    ports:
      - 80:80
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - frontend
      - backend
```
