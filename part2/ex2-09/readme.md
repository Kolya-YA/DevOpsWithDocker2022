# Exercise 2.96

## docker-compose.yml

```yml
version: "3.9"

services:
  myredis:
    image: redis
    restart: unless-stopped

  db:
    image: postgres:13-alpine
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: testpsw
    container_name: testdb
    volumes:
      - ./database:/var/lib/postgresql/data

  backend:
    build: ../../part1/ex1-13
    environment:
      - REQUEST_ORIGIN=http://frontend:5000
      - REDIS_HOST=myredis
      - POSTGRES_HOST=db
      - POSTGRES_PASSWORD=testpsw
    depends_on:
      - db

  frontend:
    build: ../../part1/ex1-12
    environment:
      - REACT_APP_BACKEND_URL=http://backend:8080

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

## nginx.conf

```nginx
events { worker_connections 1024; }

http {
  server {
    listen 80;

    location / {
      proxy_pass http://frontend:5000;
    }

    location /ping {
      proxy_set_header Host $host;
      proxy_pass http://backend:8080/ping;
    }

    location /messages {
      proxy_set_header Host $host;
      proxy_pass http://backend:8080/messages;
    }

    location /api/ {
      proxy_set_header Host $host;
      proxy_pass http://backend:8080/;
    }
  }
}
```
