---
globs: ["**/scraping/**/*.ts", "**/sync/**/*.ts"]
---

# Web Scraping Standards

## Anti-Detection (Critical)
- Rotate user agents per session
- Randomize viewport dimensions within realistic ranges
- Block analytics/tracking domains selectively — NOT all resources
- Disable HTTP/2 (some sites use it to fingerprint)
- Add human-like delays between actions (2-5 seconds)
- Simulate realistic mouse movements and scrolling

## Playwright Best Practices
- Use `page.evaluate()` with raw string functions — NOT arrow functions with closures
- NEVER use regex patterns inside template literals passed to `page.evaluate()`
  - Template literal processing corrupts backslash escapes in regex
  - Use pure string methods: `indexOf`, `substring`, `charAt`, `replace` with plain strings
- Wait for selectors before extracting (`page.waitForSelector`)
- Handle client-side rendered content (React/SPA) with explicit waits
- Set navigation timeout and retry (3 attempts with backoff)

## Data Extraction
- Extract ALL product data: name, description, prices, images, sizes, colors, specs
- Prioritize structured data sources: `window.__myx`, JSON-LD, then DOM
- For images: extract from `background-image` CSS, `<img>` tags, and JS data
- Upgrade image URLs to highest resolution available
- Validate extracted URLs before storing

## Error Handling
- Catch and log per-URL errors — don't let one failure stop the batch
- Store error messages on the `product_urls` row for user visibility
- Emit WebSocket events for real-time progress in admin UI
- Close browser sessions in `finally` blocks — never leak

## Data Storage
- Scrape → `products` table (master) + `product_variations` table (variants)
- Store full raw scraped object in `raw_data` JSONB column
- `salePrice || null` — ensure falsy values become SQL NULL
- DELETE old variations before inserting fresh ones on rescrape
