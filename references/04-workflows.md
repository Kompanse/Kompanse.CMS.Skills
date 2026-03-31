# Example Workflows

## Developing a New Website

### Step 1: Connection Setup

```bash
# MCP tool: configure_connection_with_mcp_token
{
  "baseUrl": "http://localhost:5297",  # optional
  "mcpToken": "admin-created-token",
  "timeoutMs": 30000
}
```

### Step 2: Environment Check

```bash
tenant_modules_list
tenant_languages_list
```

### Step 3: Site Settings

```bash
tenant_site_settings_update
# Site name, tagline, SEO settings, logo, social media links
```

### Step 4: Media Upload

```bash
tenant_media_upload
# Logo, banner, images - upload all to Media Manager first
```

### Step 5: Create Pages

```bash
tenant_pages_create
# about-us, contact, privacy-policy, kvkk
```

### Step 6: Create Content Sections

```bash
tenant_content_sections_create
# hero, stats, testimonials, FAQ, CTA
```

### Step 7: Create Menus

```bash
tenant_navigator_menus_create
# header-menu, footer-menu
```

### Step 8: Define Forms (if needed)

```bash
tenant_forms_create
# contact-form, quote-form
```

### Step 9: Verification

```bash
# X-Api-Key header must be sent with every Public API request
public_site_settings_get
public_pages_get_by_code
public_content_sections_get_by_key
public_navigator_menus_get_by_code
```

### Step 10: Frontend Development

- Write website code
- Fetch data from `/api/public/...` endpoints
- **X-Api-Key header must be sent with every request**

---

## Adding Blog Content

### Step 1: Categories and Tags

```bash
tenant_blog_categories_create
tenant_blog_tags_create
```

### Step 2: Blog Posts

```bash
tenant_blog_posts_create
```

### Step 3: Verification

```bash
# X-Api-Key header must be sent with every Public API request
public_blog_posts_list
```

---

## Creating Product Catalog

### Step 1: Categories

```bash
tenant_product_categories_create
```

### Step 2: Attributes

```bash
tenant_product_attribute_groups_create
tenant_product_attributes_create
```

### Step 3: Products

```bash
tenant_products_create
```

### Step 4: Verification

```bash
# X-Api-Key header must be sent with every Public API request
public_product_categories_list
public_products_list
public_products_get_filters
```

---

## Error Handling

### 401 / Unauthorized

Check:
- Was `configure_connection_with_mcp_token` called?
- Is the McpToken correct?
- Is the API running?

### 403 / Forbidden

- The relevant module may not be assigned to the tenant
- The tenant user may not have permission

### 404 / Not Found

- Wrong ID/slug/code may be sent
- The relevant resource may not have been created yet

### Media Upload Errors

- `filePath` must point to a real local file
- Maximum file size may be hitting tenant limit
