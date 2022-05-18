# Exercise 2.7

## Machine learning project

The solution in the __docker-compose.yml__

```yml
version: "3.9"

services:
  traning:
    build: https://github.com/docker-hy/ml-kurkkumopo-training.git
    volumes:
      - model:/src/model

  backend:
    build: https://github.com/docker-hy/ml-kurkkumopo-backend.git
    ports:
      - 5000:5000
    volumes:
      - model:/src/model
  
  frontend:
    build: https://github.com/docker-hy/ml-kurkkumopo-frontend.git
    ports:
      - 3000:3000

volumes:
  model:
```
