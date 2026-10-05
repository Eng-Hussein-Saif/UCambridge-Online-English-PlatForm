# Deployment

## Frontend Development

The frontend applications are React + Vite apps and are intended to be run locally in a development environment.

Typical development flow:

```bash
npm install
npm run dev
```

## Frontend Build

Production build flow is expected via:

```bash
npm run build
```

## Backend

The backend is a PHP application intended to run in a PHP-enabled web server environment such as:

- Apache
- XAMPP
- local PHP server environment

The actual backend uses:

- PHP
- MySQL
- PDO
- session-based auth

## Environment and Configuration

The project has configuration files for:

- database connection
- CORS handling
- auth checks

No secrets or credentials were copied into this documentation. Only structural configuration patterns were described.

## API URL Configuration

The frontend apps appear to target the backend through PHP endpoints served from the local server environment. The exact host configuration was not fully enumerated as a single environment file in the workspace.

## Database Setup

MySQL is expected to be available for backend operations, with PHP connecting through the configured PDO DSN in the backend config files.

## Summary

The application is structured around local PHP server hosting combined with frontend Vite app development. The documentation intentionally avoids claiming a production deployment pipeline that was not explicitly verified in the workspace.
