# [Backstage](https://backstage.io)

## Development

### Install dependencies
First run the following command to download the dependencies.

```bash
yarn install
```

### Create database

```bash
./tasks db-run
```

### Set required variables
Open the environment variable file.

```bash
vi .env/dev
```

And add the following content.

**Note**: For the Github credentials follow the backstage doc for [authentication](https://backstage.io/docs/getting-started/configuration#setting-up-authentication) and [github integration](https://backstage.io/docs/getting-started/configuration#setting-up-a-github-integration).

```bash
set -o allexport
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
POSTGRES_USER=backstage
POSTGRES_PASSWORD=backstage
GITHUB_TOKEN=ghp_xxxx
GITHUB_CLIENT_ID=xxx
GITHUB_CLIENT_SECRET=xxx
set +o allexport
```
### Run development server

```bash
./tasks dev
```

### Docker run

For building a docker image run the following command.

```bash
./tasks build
```

## Run the docker image

A docker compose file is created for deploying the app more conveniently. It starts a postgres and backstage.

First, open the environment variable file.

```bash
vi .env/docker
```
And add the following content.

**Note**: For the Github credentials follow the backstage doc for [authentication](https://backstage.io/docs/getting-started/configuration#setting-up-authentication) and [github integration](https://backstage.io/docs/getting-started/configuration#setting-up-a-github-integration).

```bash
set -o allexport
POSTGRES_PASSWORD=backstage
GITHUB_TOKEN=ghp_xxxx # Classic personal token with repo and workflow permissions
GITHUB_CLIENT_ID=xxx
GITHUB_CLIENT_SECRET=xxx
DOCKER_IMAGE_TAG=$(git rev-parse --short HEAD)
set +o allexport
```

Now it is time to run the image using docker compose.

```bash
./tasks docker-up
```

After testing the docker can be stopped by.

```bash
./tasks docker-down
```
