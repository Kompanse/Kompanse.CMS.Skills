---
name: kompanse-cms-website-developer
description: Use this skill when you want to develop a website using Kompanse CMS. Use this skill when users want content-managed web projects such as websites, landing pages, blogs, or product catalogs. Use MCP tools to manage CMS content, and Public API to display website content.
---

# Kompanse CMS Website Developer

This skill provides all the information needed to develop websites using Kompanse CMS and MCP (Model Context Protocol).

## Core Concepts

> **Agent uses MCP to manage CMS. Uses Public API to display published website content.**

- **MCP**: Used to manage CMS content (create, update, list)
- **Public API**: Used to display live website content

## Workflow

### 1. Connection Setup

Connect using McpToken:

```bash
# MCP tool: configure_connection_with_mcp_token
{
  "baseUrl": "http://localhost:5297",  # optional, default: https://cms-api.kompanse.com
  "mcpToken": "admin-created-token",
  "timeoutMs": 30000
}
```

> **McpToken**: Token created by admin and associated with a tenant. No X-Api-Key or tenant login required; the token is already associated with the tenant.

### 2. Environment Check

```bash
tenant_modules_list
tenant_languages_list
```

### 3. Content Creation (with MCP)

```bash
# In order:
tenant_site_settings_update    # Site settings
tenant_media_upload           # Upload images
tenant_pages_create          # Create pages
tenant_content_sections_create  # Create sections
tenant_navigator_menus_create   # Create menus
tenant_forms_create           # Define forms (if needed)
```

### 4. Verification (with Public API)

```bash
# X-Api-Key header must be sent with every Public API request
public_site_settings_get
public_pages_get_by_code
public_content_sections_get_by_key
public_navigator_menus_get_by_code
public_locations_geo_countries_list
```

### 5. Frontend Development

- Use feature-based architecture
- Fetch data from `/api/public/...` endpoints
- **X-Api-Key header must be sent with every request**
- Fetch and cache translations from CMS

## Module Selection Guide

| Module | For | Example Content |
|--------|-----|-----------------|
| **Pages** | Pages with independent URLs | About, Contact, Privacy |
| **Content Sections** | Page blocks | Hero, cards, testimonials, FAQ |
| **Carousel Manager** | Rotating slides | Homepage slider, campaigns |
| **Blog** | Editorial content | Blog posts, news |
| **Product Catalog** | Product lists | Products, categories, filters |
| **Navigator** | Menus | Header, footer menus |
| **Forms** | Data collection | Contact form, quote form |
| **Locations** | Store/branch locations | Stores, branches, service points |
| **Media Manager** | Files | Images, PDFs |
| **Site Settings** | General settings | Site name, SEO, logo |
| **Translations** | Translations | UI strings, labels |

## Important Rules

- ❌ Don't guess routes - use `list_route_mappings`
- ❌ No MCP tools for DELETE operations
- ❌ Don't use tenant endpoints in frontend
- ✅ Use MCP for content creation/update
- ✅ Use Public API for displaying published content
- ✅ Always upload media to Media Manager first

## Detailed Information

For more information, read the documents in the `references/` folder:

- `references/01-mcp-tools.md` - All MCP tools
- `references/02-public-api.md` - Public API endpoints
- `references/03-content-sections.md` - Content Sections details and templates
- `references/04-workflows.md` - Example workflows
- `references/05-pages.md` - Pages module
- `references/06-blog.md` - Blog module
- `references/07-product-catalog.md` - Product Catalog module
- `references/08-navigator.md` - Navigator (Menus) module
- `references/09-forms.md` - Forms module
- `references/10-translations.md` - Translations module
- `references/11-carousel.md` - Carousel Manager module
- `references/12-media.md` - Media Manager module
- `references/13-site-settings.md` - Site Settings module
- `references/14-locations.md` - Locations module
