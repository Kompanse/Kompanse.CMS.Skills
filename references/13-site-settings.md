# Site Settings Module Reference

## What Is It Used For?

General site configuration:
- Site name, tagline
- Logo, favicon
- SEO settings
- Social media links
- Contact information
- Theme settings

## Features

- **Logo / Dark Logo**: Different logos for theme
- **Favicon**: Site icon
- **Theme Color**: Brand color (meta theme-color)
- **Canonical Base URL**: Canonical URL for SEO
- **Robots Index/Follow**: Search engine settings
- **Social Links**: Platform and URL

## MCP Tools

```bash
# Get site settings
tenant_site_settings_get

# Update site settings
tenant_site_settings_update
```

## Public API

```bash
# Get site settings
GET /api/public/site-settings
```

## Site Settings Example

```json
{
  "isActive": true,
  "logoFileUrl": "https://cdn.example.com/logo.png",
  "logoDarkFileUrl": "https://cdn.example.com/logo-dark.png",
  "faviconFileUrl": "https://cdn.example.com/favicon.ico",
  "appleTouchIconUrl": "https://cdn.example.com/apple-touch.png",
  "defaultOgImageUrl": "https://cdn.example.com/og-image.png",
  "canonicalBaseUrl": "https://example.com",
  "themeColor": "#111827",
  "supportEmail": "hello@example.com",
  "supportPhone": "+1 555 000 00 00",
  "address": "Istanbul, Turkey",
  "robotsIndex": true,
  "robotsFollow": true,
  "translations": [
    {
      "languageId": "uuid-en",
      "siteName": "Example Site",
      "tagline": "The best solutions",
      "seoTitle": "Example Site",
      "seoDescription": "Description",
      "seoKeywords": "cms, headless, site",
      "ogTitle": "Example Site",
      "ogDescription": "Description",
      "footerText": "All rights reserved.",
      "copyrightText": "© 2026 Example Site"
    }
  ],
  "socialLinks": [
    {
      "platform": "LinkedIn",
      "url": "https://linkedin.com/company/example",
      "sortOrder": 1,
      "isActive": true
    },
    {
      "platform": "Twitter",
      "url": "https://twitter.com/example",
      "sortOrder": 2,
      "isActive": true
    }
  ]
}
```

## Frontend Usage

```typescript
const settings = await fetch('/api/public/site-settings', {
  headers: { 'X-Api-Key': apiKey }
}).then(r => r.json());

// Usage in HTML
<title>{settings.data.translations[0].seoTitle}</title>
<meta name="description" content="{settings.data.translations[0].seoDescription}" />
<meta name="theme-color" content="{settings.data.themeColor}" />
<link rel="icon" href="{settings.data.faviconFileUrl}" />
```
