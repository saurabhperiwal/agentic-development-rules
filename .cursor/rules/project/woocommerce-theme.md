---
globs: ["themes/**/*.php", "themes/**/*.css", "themes/**/*.js"]
---

# WordPress/WooCommerce Theme Standards

## PHP Standards
- Escape all output: `esc_html()`, `esc_attr()`, `esc_url()`, `wp_kses()`
- Sanitize all input: `sanitize_text_field()`, `absint()`, `sanitize_email()`
- Use WordPress/WooCommerce APIs — don't write raw SQL
- Prefix all function names with `flavor_` to avoid conflicts
- Use `wp_json_encode()` for JSON output

## WooCommerce Hooks
- Use WooCommerce hooks, not direct template overrides where possible
- Register AJAX handlers for both `wp_ajax_` and `wp_ajax_nopriv_`
- Load cart with `wc_load_cart()` before cart operations if `WC()->cart` is null
- Map stock status correctly: `in_stock` → `instock`, `out_of_stock` → `outofstock`

## Theme Assets
- Version ALL assets with `FLAVOR_VERSION` constant for cache busting
- Update version in BOTH `style.css` header AND `functions.php` constant
- Enqueue scripts/styles properly with `wp_enqueue_script/style`
- Use `wp_localize_script` to pass PHP data to JavaScript

## CSS
- Mobile-first responsive design
- Use CSS custom properties for theming
- `env(safe-area-inset-bottom)` for bottom safe area on mobile
- Test on: Mac Safari, Mac Chrome, iPhone Safari, Android Chrome
- Maintain cross-browser consistency

## JavaScript
- No ES6 modules (WordPress doesn't support them in enqueued scripts)
- Wrap in IIFE: `(function() { 'use strict'; ... })();`
- Use `fetch` with `credentials: 'same-origin'` for AJAX
- Update ALL cart badge locations after cart changes
- Debounce scroll event handlers

## SEO
- Proper `<title>`, `<meta description>`, canonical URLs
- Open Graph tags for social sharing (og:image, og:title, og:description)
- JSON-LD structured data for products (Schema.org Product type)
- Hidden semantic HTML for crawlers alongside visual UI
- `alt` attributes on all images
