# Opcion 1: Bitbucket + Jira + Pipelines

## Flujo

1. Crear/usar issue Jira: `SUM-1`.
2. Crear rama: `feature/SUM-1-sudoku-base`.
3. Commits con clave Jira: `SUM-1 ...`.
4. Abrir PR hacia `main`.
5. `bitbucket-pipelines.yml` ejecuta tests.
6. Paso de deploy staging (placeholder) para integrar Vercel/Render/SSH.

## Comandos locales

```bash
composer install
composer test
php -S localhost:8080 -t public
```
