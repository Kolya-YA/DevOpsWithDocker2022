# Exercise 3.4

## Fronend

    ~/***/ex3-04/frontend (master*) » docker images                                                                                      

    REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
    frontend     small     d49dc1a4b9a8   About a minute ago   496MB

### Dockerfile

    FROM node:lts-slim
    EXPOSE 5000

    WORKDIR /usr/src/app
    COPY . .

    RUN npm install; \
        npm run build; \
        npm install -g serve; \
        useradd -m appuser; \
        chown appuser .

    CMD serve -s -l 5000 build

## Backend

    # ~/***/ex3-04/backend (master*) » docker images
    # REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
    # backend      small     6212f75e2af2   4 minutes ago   366MB

### Dockerfile

    FROM ubuntu:18.04
    EXPOSE 8080
    WORKDIR /usr/src/app
    COPY . .
    ENV PATH /usr/local/go/bin:$PATH

    RUN apt-get update; \
        apt-get install -y wget; \
        wget -c -P /usr/local https://go.dev/dl/go1.18.2.linux-amd64.tar.gz; \
        tar -C /usr/local -xzf /usr/local/go1.18.2.linux-amd64.tar.gz; \
        go build; \
      apt-get purge -y --auto-remove wget;\
        rm -rf /usr/local/go; \
        rm -rf /var/lib/apt/lists/*; \
        useradd -m appuser; \
        chown appuser .

    USER appuser
    CMD ./server