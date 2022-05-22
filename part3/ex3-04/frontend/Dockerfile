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

# ~/DevOpsWithDocker2022/part3/ex3-04/frontend (master*) » docker images                                                                                                                              kolya_ya@Mac-mini-Ya
# REPOSITORY   TAG       IMAGE ID       CREATED              SIZE
# frontend     small     d49dc1a4b9a8   About a minute ago   496MB