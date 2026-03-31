# Navigator (Menus) Module Reference

## What Is It Used For?

Site navigation:
- Header menu
- Footer menu
- Submenus
- Mega menu structures

## Structure

- **Menu**: A menu group (header, footer, etc.)
- **Menu Item**: Items within the menu (tree structure)
  - `title`: Visible text
  - `link`: Target URL
  - `children`: Submenu items
  - `openInNewTab`: Open in new tab?

## MCP Tools

```bash
# List menus
tenant_navigator_menus_list

# Get menu detail
tenant_navigator_menus_get

# Create menu
tenant_navigator_menus_create

# Update menu
tenant_navigator_menus_update
```

## Public API

```bash
# Get menu by code
GET /api/public/navigator/menus/{code}
```

## Menu Creation Example

```json
{
  "code": "header-main",
  "name": "Main Menu",
  "isActive": true,
  "items": [
    {
      "sortOrder": 1,
      "openInNewTab": false,
      "translations": [
        {
          "languageId": "uuid-en",
          "title": "Products",
          "link": "/products"
        }
      ],
      "children": [
        {
          "sortOrder": 1,
          "translations": [
            {
              "languageId": "uuid-en",
              "title": "Software",
              "link": "/products/software"
            }
          ]
        },
        {
          "sortOrder": 2,
          "translations": [
            {
              "languageId": "uuid-en",
              "title": "Hardware",
              "link": "/products/hardware"
            }
          ]
        }
      ]
    },
    {
      "sortOrder": 2,
      "translations": [
        {
          "languageId": "uuid-en",
          "title": "About Us",
          "link": "/about-us"
        }
      ]
    },
    {
      "sortOrder": 3,
      "translations": [
        {
          "languageId": "uuid-en",
          "title": "Contact",
          "link": "/contact"
        }
      ]
    }
  ]
}
```

## Behavior Notes

- Only menus and items with `isActive = true` are returned
- If translation for requested language is missing, fallback to default language is applied
- Items with `link = null` can be used as containers
