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

```bash
set -o allexport
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
POSTGRES_USER=backstage
POSTGRES_PASSWORD=backstage
GITHUB_TOKEN=ghp_xxxx # Classic personal token with repo and workflow permissions
GITHUB_CLIENT_ID=xxx
GITHUB_CLIENT_SECRET=xxx
set +o allexport
```
### Run development server

```bash
./tasks dev
```
