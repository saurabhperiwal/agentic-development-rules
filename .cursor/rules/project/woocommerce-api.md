---
globs: ["**/woocommerce/**/*.ts"]
---

# WooCommerce API Integration Rules

## Product Publishing Pipeline
1. Fetch product + variations + images from our DB
2. Convert currency: `sourcePrice * exchangeRate`
3. Apply markup: `convertedPrice * (1 + markupPercent/100)`
4. Create/update product in WooCommerce (Phase 1: no images)
5. Upload images one-by-one (Phase 2: avoids Cloudflare 524 timeout)
6. Create/update variations with proper attribute matching

## Variation Sync (Critical — Was a Recurring Bug)
- Build a signature map of existing WooCommerce variations (attribute combos)
- Match by signature: if match exists → `wooPut` (update), else → `wooPost` (create)
- Delete orphaned WooCommerce variations not in our DB: `wooDelete` with `?force=true`
- NEVER delete-all-and-recreate — it breaks WooCommerce order references

## Handling Stale References
- If `wooPut` returns "Invalid ID" or 404 → product was deleted externally
- Clear stale `woo_product_id` from `published_products` table
- Retry as `wooPost` (create fresh product)
- Log the recovery for audit trail

## Image Handling
- Validate image URLs before sending (must have valid hostname)
- Upload images one at a time to prevent timeout
- Filter out tracking pixels and non-product images
- Prefer highest resolution available

## Attribute Management
- Create/reuse WooCommerce attributes via the REST API
- Create attribute terms before assigning to variations
- Map scraper attribute names to WooCommerce-compatible slugs
- Case-insensitive matching for terms

## Error Handling
- 90-second timeout on all WooCommerce API calls
- Truncate error response bodies in logs (Cloudflare returns huge HTML)
- Retry transient errors (5xx) with backoff
- Permanent errors (4xx): log, skip, continue with next product
