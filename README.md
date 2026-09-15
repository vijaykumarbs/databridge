# DataBridge

**Zero-server master data import tool.** Transforms and validates data from any source format (CSV, XLS, XLSX) into your required output schema — entirely in the browser. No backend. No data leaves the user's machine.

## What it does

Operations and IT teams routinely receive master data from multiple vendors in inconsistent formats. DataBridge lets you:

1. Upload one or more CSV/XLS/XLSX files (up to 50,000 rows each)
2. Define your target output schema (column names, types, required flags)
3. Add validation rules (email, numeric, date, max length, regex)
4. Transform and download — valid rows clean, error rows flagged with an extra `_validation_errors` column

Optional: connect your own Anthropic or OpenAI API key for smart column mapping when source headers don't match your target schema.

## Deploy in 60 seconds

### GitHub Pages (free)

1. Fork this repo
2. Go to **Settings → Pages → Source → Deploy from branch → main / root**
3. Your tool is live at `https://yourusername.github.io/databridge`

### Cloudflare Pages (free, faster)

1. Go to [pages.cloudflare.com](https://pages.cloudflare.com)
2. Connect your GitHub repo or drag-drop the `index.html`
3. Done — you get a `*.pages.dev` URL and can add a custom domain

### Offline / air-gapped

Just open `index.html` in any modern browser. No server required. Works fully offline (LLM mapping needs internet only when you enter an API key).

## Customise for your client

Edit these lines at the top of `index.html`:

```html
<title>DataBridge — Master Data Import Tool</title>   <!-- change to client name -->
<meta name="description" content="...">               <!-- update description -->
```

And this in the header:
```html
<div class="h-logo">Data<span>Bridge</span></div>     <!-- swap branding -->
<a class="h-link" href="https://github.com/YOUR_USERNAME/databridge">GitHub ↗</a>
```

## LLM cost

LLM is called **once per source file** (not per row) to detect column mappings. Using Claude Haiku: ~$0.0003 per file. Using GPT-4o mini: ~$0.0002 per file. For most implementations the cost is negligible.

Your API key is stored in `localStorage` only and sent directly to the LLM provider. DataBridge has no backend and cannot access your key.

## Browser support

Chrome 90+, Firefox 88+, Safari 15+, Edge 90+.

## Roadmap ideas

- Value transformation rules (uppercase, date format normalisation, lookup tables)
- Google Sheets export
- Saved schema profiles (named, switchable)
- Multi-sheet XLSX support
- Column mapping preview before full transform

## License

MIT — use freely, modify, redistribute, white-label for clients.
