# DataBridge

ERP implementations repeatedly reach the same data-readiness bottleneck: vendor, legacy, and business-owned files use inconsistent headers and formats, while teams reconcile mappings and repair rows in spreadsheets before migration or cutover. That manual workaround consumes analyst time, makes validation hard to repeat, and obscures which rows are still unsafe to load.

DataBridge is a browser-based utility for defining a target schema, mapping source columns, applying row-level validation, and exporting an XLSX file with errors flagged. Its goal is to make this preparation step reviewable and repeatable. The app is the delivery vehicle; the product decisions and pilot criteria are in [PRODUCT.md](PRODUCT.md).

**Current evidence status:** this repository does not yet document a partner or internal pilot. Do not interpret the problem statement as measured savings or customer validation. A pilot plan and baseline measures are included in `PRODUCT.md`.

## Run locally

Open `index.html` in a modern browser. The parser libraries are included in `vendor/`; core mapping, validation, and export work without a network connection. Optional AI mapping requires internet access and a key for Anthropic or OpenAI. For a local HTTP origin, run `./run-local.sh` (Python 3) and open `http://127.0.0.1:4173`.

## Workflow

1. Upload one or more source files (up to 50,000 rows per file).
2. Define the target columns or import a JSON schema.
3. Configure validation rules and, optionally, AI assisted column mapping.
4. Review the result summary and download all, valid, or error rows.

## Data and security

- Files are parsed and transformed in the browser. There is no DataBridge server or database.
- AI mapping is optional. When enabled, up to three sample rows and source/target headers for each file are sent directly to the selected provider with the user's key. The provider's data handling and billing terms apply.
- The key, schema, and validation rules are stored in origin-scoped browser `localStorage`. This storage is plaintext and accessible to the browser profile and same-origin scripts. Remove the key in browser storage or clear site data when finished.
- Never use a shared or managed provider key in this public static client. A managed service requires an authenticated backend and server-side secret storage.
- Treat exports as untrusted until reviewed. Validate mappings and errors before using data in operational systems.

## System design

See [architecture and security decisions](docs/architecture.md), [deployment](docs/deployment.md), and [vendored dependencies](vendor/README.md). The application is a static, browser-only MVP with no build step or server-side tier.

## Deployment

The repository includes a GitHub Actions workflow that publishes the static site from `main` to GitHub Pages. Configure GitHub Pages to use GitHub Actions in repository settings. Deployment is public; do not commit keys or customer files.

## License

MIT. Third-party dependency licenses are included alongside the vendored bundles.
