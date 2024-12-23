# Create a running db instance via docker

Set up a postgres server instance and client via docker compose.

```shell
services:

  postgres-db:
    image: postgres:15
    container_name: taco-cloud-db
    restart: on-failure
    environment:
      - POSTGRES_USER=tacouser
      - POSTGRES_PASSWORD=tacopassword
      - POSTGRES_DB=tacocloud
    ports:
      - "5432:5432"
    volumes:
      - postgres-db:/var/lib/postgresql/data

  adminer:
    image: adminer
    restart: on-failure
    ports:
      - "3000:8080"

volumes:
  postgres-db:

```

Run with profile `prod`

```bash
java -jar -Dspring.profiles.active=prod target/taco-cloud-0.0.1-SNAPSHOT.jar
```

Run with profile `prod` via maven

```bash
mvn spring-boot:run -Dspring-boot.run.profiles=prod
```
