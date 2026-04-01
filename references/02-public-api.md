# Public API Reference

**X-Api-Key header is required for all Public API endpoints** (except media endpoint).

## Endpoint Structure

### Languages

| Endpoint | Description |
|----------|-------------|
| `GET /api/public/languages` | Lists active languages |

### Site Settings

| Endpoint | Description |
|----------|-------------|
| `GET /api/public/site-settings` | Gets site settings (logo, SEO, social links) |

### Pages

| Endpoint | Description | Query Parameters |
|----------|-------------|-------------------|
| `GET /api/public/pages` | Lists pages | `page`, `pageSize`, `search`, `lang` |
| `GET /api/public/pages/by-slug/{slug}` | Gets page by slug | `lang` |
| `GET /api/public/pages/by-code/{code}` | Gets page by code | `lang` |

### Content Sections

| Endpoint | Description | Query Parameters |
|----------|-------------|-------------------|
| `GET /api/public/content-sections/by-key/{code}` | Gets section by code | `lang` |
| `POST /api/public/content-sections/by-keys` | Gets multiple sections | `codes[]`, `lang` |

### Carousel Manager

| Endpoint | Description | Query Parameters |
|----------|-------------|-------------------|
| `GET /api/public/carousel-manager/carousels/{code}` | Gets carousel by code | `lang` |

### Navigator (Menus)

| Endpoint | Description | Query Parameters |
|----------|-------------|-------------------|
| `GET /api/public/navigator/menus/{code}` | Gets menu by code | `lang` |

### Blog

| Endpoint | Description | Query Parameters |
|----------|-------------|-------------------|
| `GET /api/public/blog/categories` | Lists blog categories | - |
| `GET /api/public/blog/tags` | Lists blog tags | - |
| `GET /api/public/blog/posts` | Lists blog posts | `page`, `pageSize`, `categoryId`, `tagId`, `search`, `lang` |
| `GET /api/public/blog/posts/{slug}` | Gets blog post by slug | `lang` |

### Product Catalog

| Endpoint | Description | Query Parameters |
|----------|-------------|-------------------|
| `GET /api/public/product-catalog/categories` | Product categories (hierarchical) | - |
| `GET /api/public/product-catalog/products` | Lists products | `page`, `pageSize`, `categoryId`, `search`, `lang`, `attrs[code]` (repeatable), `attrs[code_min]`, `attrs[code_max]` |
| `GET /api/public/product-catalog/products/{slug}` | Gets product detail by slug | `lang` |
| `GET /api/public/product-catalog/products/filters` | Gets filter definitions | - |

### Forms

| Endpoint | Description |
|----------|-------------|
| `POST /api/public/forms/{code}/submit` | Form submission |

### Translations

| Endpoint | Description |
|----------|-------------|
| `GET /api/public/translations` | Translations in all languages |
| `GET /api/public/translations/{languageCode}` | Translations in specific language |

### Media

| Endpoint | Description | Authorization |
|----------|-------------|----------------|
| `GET /media/{customerSlug}/{fileName}` | Media file (public ones) | **Not Required** |

---

## Frontend Integration

```typescript
// ✅ Correct - Use Public endpoint
// ⚠️ X-Api-Key header must be sent with every request (except media)

const apiKey = 'tenant-api-key';

const response = await fetch('/api/public/pages', {
  headers: {
    'X-Api-Key': apiKey
  }
});
```

### Example: Content Sections (Multiple)

```typescript
// POST /api/public/content-sections/by-keys
const sections = await fetch('/api/public/content-sections/by-keys', {
  method: 'POST',
  headers: {
    'X-Api-Key': apiKey,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    codes: ['home-hero', 'home-features', 'home-stats'],
    lang: 'en'
  })
}).then(res => res.json());
```

### Example: Product Filtering

```typescript
// Filtered product list
const products = await fetch(
  '/api/public/product-catalog/products?categoryId=xxx&attrs[color]=Blue&attrs[color]=Black&attrs[size]=M&attrs[size]=L&lang=en',
  {
    headers: { 'X-Api-Key': apiKey }
  }
).then(res => res.json());

// Filter definitions (for filter panel)
const filters = await fetch('/api/public/product-catalog/products/filters', {
  headers: { 'X-Api-Key': apiKey }
}).then(res => res.json());
```

Filtering semantics:
- Repeated selections within the same attribute are evaluated with `OR`.
- Different attribute groups are combined with `AND`.

Example logic:
`attrs[color]=Blue&attrs[color]=Black&attrs[size]=M&attrs[size]=L`
means `(color IN [Blue, Black]) AND (size IN [M, L])`.

### Example: Blog Listing

```typescript
// Paginated blog list
const blogs = await fetch(
  '/api/public/blog/posts?page=1&pageSize=10&categoryId=xxx&lang=en',
  {
    headers: { 'X-Api-Key': apiKey }
  }
).then(res => res.json());
```

## Public Tools (MCP)

| Tool | Description |
|------|-------------|
| `public_languages_list` | Lists active languages |
| `public_site_settings_get` | Gets site settings |
| `public_pages_list` | Lists pages |
| `public_pages_get_by_slug` | Gets page by slug |
| `public_pages_get_by_code` | Gets page by code |
| `public_content_sections_get_by_key` | Gets section by code |
| `public_content_sections_get_by_keys` | Gets multiple sections |
| `public_carousel_manager_carousels_get_by_code` | Gets carousel by code |
| `public_navigator_menus_get_by_code` | Gets menu by code |
| `public_blog_categories_list` | Lists blog categories |
| `public_blog_tags_list` | Lists blog tags |
| `public_blog_posts_list` | Lists blog posts |
| `public_blog_posts_get_by_slug` | Gets blog post by slug |
| `public_product_categories_list` | Lists product categories |
| `public_products_list` | Lists products |
| `public_products_get_by_slug` | Gets product by slug |
| `public_products_get_filters` | Gets filters |
| `public_forms_submit` | Submits form |
| `public_media_download` | Downloads media file |
| `public_translations_list` | Gets translations for specific language |
| `public_translations_all` | Gets translations for all languages |
