# Carousel Manager Module Reference

## What Is It Used For?

Rotating content blocks:
- Homepage sliders
- Campaign banners
- Promotional carousels

## Structure

- **Carousel**: Main record (code, name, isActive)
- **Carousel Item**: Slides
  - Desktop image
  - Mobile image
  - Title, subtitle
  - CTA (text + link)
  - Publish date range

## MCP Tools

```bash
# Create carousel
tenant_carousel_manager_carousels_create

# List carousels
tenant_carousel_manager_carousels_list

# Get carousel detail
tenant_carousel_manager_carousels_get

# Get carousel by code
tenant_carousel_manager_carousels_get_by_code

# Update carousel
tenant_carousel_manager_carousels_update

# Add item
tenant_carousel_manager_carousel_items_create

# Get item detail
tenant_carousel_manager_carousel_items_get

# Update item
tenant_carousel_manager_carousel_items_update
```

## Public API

```bash
# Get carousel by code
GET /api/public/carousel-manager/carousels/{code}
```

## Carousel Example

```json
{
  "code": "home-hero",
  "name": "Homepage Hero",
  "isActive": true,
  "items": [
    {
      "desktopImageMediaFileId": "uuid-desktop",
      "mobileImageMediaFileId": "uuid-mobile",
      "sortOrder": 1,
      "isActive": true,
      "publishStartDate": "2026-01-01T00:00:00Z",
      "publishEndDate": "2026-12-31T23:59:59Z",
      "openInNewTab": false,
      "translations": [
        {
          "languageId": "uuid-en",
          "title": "New Season Collection",
          "subtitle": "Discover the campaign",
          "ctaText": "Explore",
          "ctaLink": "/campaigns/new-season",
          "altText": "New season banner"
        }
      ]
    }
  ]
}
```

## Publish Filtering

In Public API, only items with the following are returned:
- `isActive = true`
- `publishStartDate` is empty or in the past
- `publishEndDate` is empty or in the future

## Language Fallback

- If translation for requested language is missing, fallback to default language
- If also missing in default language, the first available translation is used
