# Pages Module Reference

## What Is It Used For?

Creating pages with independent URLs:
- About, Contact, Privacy Policy
- Landing pages
- Corporate pages
- Static content pages

## Pages vs Content Sections

| Feature | Pages | Content Sections |
|---------|-------|------------------|
| Full page management | ✅ | ❌ |
| Page block management | ❌ | ✅ |
| URL/Slug support | ✅ | ❌ |
| Template-based component | ❌ | ✅ |
| Repeating card structures | ❌ | ✅ |

## Key Features

- **Code**: Unique identifier (e.g., `about-us`)
- **Slug**: Part shown in URL (can vary by language)
- **Status**: `Draft`, `Published`, `Archived`
- **Multi-language support**: Separate translation for each language

## MCP Tools

```bash
# Create new page
tenant_pages_create

# List pages
tenant_pages_list

# Get page by ID
tenant_pages_get

# Get page by code
tenant_pages_get_by_code

# Update page
tenant_pages_update
```

## Public API

```bash
# List all pages
GET /api/public/pages

# Get page by slug
GET /api/public/pages/by-slug/{slug}

# Get page by code
GET /api/public/pages/by-code/{code}
```

## Page Creation Example

```json
{
  "body": {
    "code": "about-us",
    "status": "Published",
    "isActive": true,
    "noIndex": false,
    "coverImageMediaFileId": "uuid-value",
    "translations": [
      {
        "languageId": "uuid-en",
        "title": "About Us",
        "description": "Brief info about our company",
        "content": "<p>Our company was established in 2010...</p>",
        "slug": "about-us",
        "metaTitle": "About Us | Company Name",
        "metaDescription": "Detailed information about our company.",
        "metaKeywords": "about us, company, history"
      }
    ]
  }
}
```

## URL Structure

| Language | URL |
|----------|-----|
| EN | `/about-us` |
| TR | `/hakkimizda` |
| DE | `/ueber-uns` |

Using **code** instead of slug is recommended in frontend (stays constant).
