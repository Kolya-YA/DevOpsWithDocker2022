FROM node:lts-slim
EXPOSE 5000
RUN node -v && npm -v
WORKDIR /usr/src/app
COPY . .
RUN npm install
RUN npm run build
RUN npm install -g serve

RUN useradd -m appuser

RUN chown -R appuser /usr/src/app
USER appuser

CMD serve -s -l 5000 build