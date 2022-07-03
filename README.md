# Instalando Keycloak com Docker-Compose


Docker-Compose
```
version: '3'

volumes:
  postgres_data:
    driver: local

services:
  postgres:
    image: postgres:latest
    volumes:
      - postgres_data:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: keycloak
      POSTGRES_USER: keycloak
      POSTGRES_PASSWORD: password
    ports:
      - 5432:5432
  keycloak:
    image: jboss/keycloak:latest
    environment:
      DB_VENDOR: POSTGRES
      DB_ADDR: postgres
      DB_DATABASE: keycloak
      DB_USER: keycloak
      DB_SCHEMA: public
      DB_PASSWORD: password
      KEYCLOAK_USER: admin
      KEYCLOAK_PASSWORD: password
    ports:
      - 8080:8080
    depends_on:
      - postgres
``` 

Research site links for docker-compose configuration:

Link Keycloak - https://www.keycloak.org/

Link GitHub Keycloac - https://github.com/keycloak/keycloak

https://www.keycloak.org/getting-started/getting-started-docker


