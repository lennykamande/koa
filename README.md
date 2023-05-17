# KOA API

**Python version: ^3.9**

### Architecture
We are using an MVC architecture i.e Model - Dao - Views/Routes, with every feature belong in its own package.
[docs](docs) folder

### Stack
- Django
- DjangoRestFramework
- Postgres

### Setup
1. Ensure you have postgres 12 setup locally
2. Install dependencies using `poetry install`
3. Copy `.env.local.example` to `.env.local` and set the appropriate values
4. Run `./migrate-new.sh` to set up the schema locally (**Note**: This is only needs to be run once. For running migrations uses `./migrate.sh`).
5. Run `./migrate.sh` to run data migrations.
6. Run `export $(grep -v '^#' .env.local | xargs)` to set up the environment variables
7. Run the server locally with `./run.sh`
8. Use `./script/lint.sh` for type checks and `./script/format.sh` for code formatting.
9. To run tests, run `./script/test.sh`

### Docker Setup
**Note:** Make sure you have [docker](https://docs.docker.com/get-started/) and [docker-compose](https://docs.docker.com/compose/) installed.

1. Run `make docker.migrate-new` to set up the schema (**Note**: You only need to run this once)
3. Run `make docker.run` to bring to up local development server.
4. Run `make docker.format` to format code using black.
5. Run `make docker.lint` to lint the code.
6. Run `make docker.test` to run all tests or `make docker.test  app/users/tests` specific tests.
