---
globs: ["**/woocommerce/**/*.ts", "**/routes/products*", "**/sync/products*", "**/currency/**/*.ts", "**/shared/utils/**"]
---

# Price Handling Rules (CRITICAL — Recurring Bug Area)

## Parsing Prices from Database
- DB `DECIMAL` columns come back as strings in node-postgres
- NEVER use truthy check on price: `if (price)` fails when price is `"0"`
- ALWAYS parse explicitly:
  ```
  const raw = row.sale_price != null ? parseFloat(row.sale_price) : null;
  const salePrice = (raw !== null && !isNaN(raw) && raw > 0) ? raw : null;
  ```

## Sending Prices to WooCommerce
- ALWAYS send both `regular_price` and `sale_price` in every update
- To clear sale price: send `sale_price: ''` (empty string) — NOT omit the field
- WooCommerce ignores omitted fields on PUT (keeps old value)
- Send prices on parent product AND on every variation

## Variable Products
- Parent product's `base_price` and `sale_price` are the SINGLE source of truth
- When publishing variations, use the parent's prices — not the variation table's stale values
- When user saves a price, cascade to `product_variations` table too

## Currency Conversion + Markup
- Flow: `sourcePrice * exchangeRate * (1 + markupPercent/100)` = finalPrice
- Apply same formula to sale price (if it exists)
- Round to 2 decimal places at the END, not in intermediate steps
- Log the full calculation: base, sale, source currency, target currency, rate, markup, final

## Price Save Endpoint
- MUST update `products.base_price` AND `products.sale_price`
- MUST cascade to `product_variations.price` AND `product_variations.sale_price`
- Validate: `salePrice` must be null OR less than `basePrice`

## WooCommerce Product Lifecycle
- If WooCommerce returns "Invalid ID" on update, clear stale `woo_product_id` and create fresh
- On republish: re-read prices from DB (not from cached data)
- On rescrape: scraper overwrites DB prices — this is intentional
