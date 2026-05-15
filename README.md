# Opcion 1: Bitbucket + Jira + Pipelines

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

## Comandos locales

```bash
composer install
composer test
php -S localhost:8080 -t public
```
