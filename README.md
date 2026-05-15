# Opcion 1: Bitbucket + Jira + Pipelines

> Estado actual: este repositorio esta alojado en GitHub.
> El flujo Bitbucket/Jira se mantiene como simulacion de proceso enterprise.

## Flujo

1. Crear/usar issue Jira: `SUM-1`.
2. Crear rama: `feature/SUM-1-sudoku-base`.
3. Commits con clave Jira: `SUM-1 ...`.
4. Abrir PR hacia `develop`.
5. Pipeline tipo Bamboo por etapas:
	- `1) Quality Gate`
	- `2) Build + Unit Tests`
	- `3) Package Artifact`
	- `4) Deploy Staging` (en `develop` y `release`)
	- `5) Smoke Test Staging`
	- `6) Approve + Deploy Production` (manual, en `release/main`)
6. Merge `develop -> release -> main` con aprobaciones.

## Activar despliegue real en GitHub

Configura en GitHub (Repo Settings):

1. Secrets
	- `REPO1_RENDER_STAGING_DEPLOY_HOOK`
	- `REPO1_RENDER_PRODUCTION_DEPLOY_HOOK`
2. Variables
	- `REPO1_STAGING_URL` (ej: `https://sudoku-repo1-staging.onrender.com`)
	- `REPO1_PRODUCTION_URL` (ej: `https://sudoku-repo1.onrender.com`)
3. Environments
	- `staging`
	- `production` (con required reviewers para gate manual)

Workflow ejecutable en repo:

- `.github/workflows/pipeline-sim.yml`

## Comandos locales

```bash
composer install
composer test
php -S localhost:8080 -t public
```
