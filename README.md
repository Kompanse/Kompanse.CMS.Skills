# Kompanse CMS Website Developer Skill

This skill provides AI agents with all the information needed to develop websites using Kompanse CMS.

## Installing This Skill

### For Open Code

```bash
npx skills add Kompanse/Kompanse.CMS.Skills
```

The skill is automatically used when:
- You ask to develop a website
- You need to manage CMS content
- You want to create landing pages, blogs, or product catalogs

### MCP Server Setup

This skill requires the Kompanse CMS MCP server to be configured. The MCP server connects to your CMS instance.

## Adding MCP Server to AI Tools

### Claude Code

```bash
claude mcp add kompanse-cms -- \
  curl https://mcp.kompanse.com/mcp
```

### Open Code

Create an `opencode.config.json` file in the project root:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "kompanse-cms-mcp": {
      "type": "remote",
      "url": "https://mcp.kompanse.com/mcp",
      "enabled": true
    }
  }
}
```

### Cursor / Windsurf

Add to `settings.json`:

```json
{
  "mcpServers": {
    "kompanse-cms": {
      "url": "https://mcp.kompanse.com/mcp"
    }
  }
}
```

## Core Concepts

- **MCP**: Used to manage CMS content (create, update, list)
- **Public API**: Used to display live website content
- **X-Api-Key**: Required on every Public API request (except media download)
- **McpToken**: Token created by admin and associated with a tenant

## Connection Setup

### McpToken Method

Uses a token created from the admin panel. No X-Api-Key or password required.

```bash
configure_connection_with_mcp_token
{
  "baseUrl": "http://localhost:5297",  # optional, default: https://cms-api.kompanse.com
  "mcpToken": "admin-created-token",
  "timeoutMs": 30000
}
```

## Quick Start

### 1. Connection Setup

Use the McpToken method shown above.

### 2. Environment Check

```bash
tenant_modules_list       # List active modules
tenant_languages_list    # List languages
```

### 3. Content Creation

```bash
# In order:
tenant_site_settings_update      # Site settings
tenant_media_upload             # Upload images
tenant_pages_create            # Create pages
tenant_content_sections_create # Create sections
tenant_navigator_menus_create  # Create menus
tenant_forms_create            # Define forms (if needed)
```

### 4. Verification

```bash
# X-Api-Key header must be sent with every Public API request
public_site_settings_get
public_pages_get_by_code
public_content_sections_get_by_key
public_locations_geo_countries_list
```

## Modules

| Module | Description | Reference |
|--------|-------------|-----------|
| Pages | Pages with independent URLs | `05-pages.md` |
| Content Sections | Page blocks (hero, cards, FAQ...) | `03-content-sections.md` |
| Carousel Manager | Rotating slides | `11-carousel.md` |
| Blog | Editorial content | `06-blog.md` |
| Product Catalog | Products, categories, filters | `07-product-catalog.md` |
| Navigator | Menus | `08-navigator.md` |
| Forms | Data collection | `09-forms.md` |
| Locations | Store/branch locations | `14-locations.md` |
| Media Manager | File management | `12-media.md` |
| Site Settings | General settings | `13-site-settings.md` |
| Translations | Translations | `10-translations.md` |

## References

For detailed information, see the `references/` folder:

### Core References

- `01-mcp-tools.md` - All MCP tools (list)
- `02-public-api.md` - Public API endpoints
- `04-workflows.md` - Example workflows

### Module References

- `03-content-sections.md` - Content Sections details and templates
- `05-pages.md` - Pages module details
- `06-blog.md` - Blog module details
- `07-product-catalog.md` - Product Catalog module details
- `08-navigator.md` - Navigator module details
- `09-forms.md` - Forms module details
- `10-translations.md` - Translations module details
- `11-carousel.md` - Carousel Manager module details
- `12-media.md` - Media Manager module details
- `13-site-settings.md` - Site Settings module details
- `14-locations.md` - Locations module details

## Rules

### Must Do

- ✅ Use MCP for content creation/update
- ✅ Use Public API for displaying published content
- ✅ Always upload media to Media Manager first
- ✅ Send X-Api-Key header in Public API requests
- ✅ Use `list_route_mappings` to check endpoint mappings when needed
- ✅ Add translations for each language

### Must Not Do

- ❌ Don't guess routes - use `list_route_mappings`
- ❌ No MCP tools for DELETE operations (soft delete is used)
- ❌ Don't use tenant endpoints in frontend
- ❌ Don't make requests without X-Api-Key (except public media)

## Troubleshooting

### 401 Unauthorized

- Was `configure_connection_with_mcp_token` called?
- Is the McpToken valid?
- Is the API running?

### 403 Forbidden

- The relevant module may not be assigned to the tenant

### 404 Not Found

- Wrong ID/slug/code may be sent
- The resource may not have been created yet

For more information: `04-workflows.md`
