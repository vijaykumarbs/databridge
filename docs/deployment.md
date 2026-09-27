# Deployment and operations

## Local use

The simplest option is to open `index.html` in a modern browser. For a loopback HTTP origin, use `./run-local.sh`; Python 3 is required. The script binds only to `127.0.0.1:4173`. Stop it with Ctrl+C.

The application has no build step and no runtime CDN requirement. Keep `index.html`, `src/`, and `vendor/` together when moving or hosting the application.

## GitHub Pages

The included workflow publishes the repository root from the `main` branch. In GitHub repository settings, set **Pages → Build and deployment → Source** to **GitHub Actions**. Each push to `main` publishes the static files. The site is public; never commit API keys or customer data.

## Other static hosts

Serve the repository root over HTTPS and preserve the `src/` and `vendor/` paths. No server variables, database, or build commands are required. Verify the host sends the page's CSP meta policy and supports the application's relative asset paths.

## Managed or shared service

Before providing shared credentials or team accounts, add an authenticated backend. Keep provider secrets in a server-side secret manager, enforce authorization and quotas, limit request size, redact logs, and define retention and deletion behavior. A browser application cannot protect a key from its user.

## Dependency maintenance

Versions and license locations are recorded in [vendor/README.md](../vendor/README.md). Review upstream security advisories and release notes before upgrading a vendored dependency. Update its license file and this inventory with each version change.
