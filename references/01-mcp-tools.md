# MCP Tool Reference

## Session Management

| Tool | Description |
|------|-------------|
| `configure_connection_with_mcp_token` | Establishes CMS connection (using McpToken) |
| `get_configuration_status` | Shows current connection status |
| `clear_configuration` | Clears the session |
| `list_route_mappings` | Shows which endpoints tools correspond to |

## Languages

| Tool | Description |
|------|-------------|
| `tenant_languages_list` | Lists active languages |
| `tenant_languages_create` | Adds new language |
| `tenant_languages_update` | Updates language info |
| `tenant_languages_set_default` | Sets default language |

## Pages

| Tool | Description |
|------|-------------|
| `tenant_pages_create` | Creates new page |
| `tenant_pages_list` | Lists pages |
| `tenant_pages_get` | Gets page by ID |
| `tenant_pages_get_by_code` | Gets page by code |
| `tenant_pages_update` | Updates page |

## Popups

| Tool | Description |
|------|-------------|
| `tenant_popups_create` | Creates popup |
| `tenant_popups_list` | Lists popups |
| `tenant_popups_get` | Gets popup by ID |
| `tenant_popups_get_by_code` | Gets popup by code |
| `tenant_popups_update` | Updates popup |
| `tenant_popups_delete` | Deletes popup |

## Content Sections

| Tool | Description |
|------|-------------|
| `tenant_content_sections_templates_list` | Lists available templates |
| `tenant_content_sections_templates_get_by_code` | Gets template details |
| `tenant_content_sections_create` | Creates new section |
| `tenant_content_sections_list` | Lists sections |
| `tenant_content_sections_get` | Gets section |
| `tenant_content_sections_get_by_code` | Gets section by code |
| `tenant_content_sections_update` | Updates section |

## Carousel Manager

| Tool | Description |
|------|-------------|
| `tenant_carousel_manager_carousels_create` | Creates carousel |
| `tenant_carousel_manager_carousels_list` | Lists carousels |
| `tenant_carousel_manager_carousels_get` | Gets carousel |
| `tenant_carousel_manager_carousels_get_by_code` | Gets carousel by code |
| `tenant_carousel_manager_carousels_update` | Updates carousel |
| `tenant_carousel_manager_carousel_items_create` | Adds slide |
| `tenant_carousel_manager_carousel_items_get` | Gets slide |
| `tenant_carousel_manager_carousel_items_update` | Updates slide |

## Blog

| Tool | Description |
|------|-------------|
| `tenant_blog_categories_create` | Creates category |
| `tenant_blog_categories_list` | Lists categories |
| `tenant_blog_categories_get` | Gets category |
| `tenant_blog_categories_update` | Updates category |
| `tenant_blog_tags_create` | Creates tag |
| `tenant_blog_tags_list` | Lists tags |
| `tenant_blog_tags_get` | Gets tag |
| `tenant_blog_tags_update` | Updates tag |
| `tenant_blog_posts_create` | Creates blog post |
| `tenant_blog_posts_list` | Lists blog posts |
| `tenant_blog_posts_get` | Gets blog post |
| `tenant_blog_posts_update` | Updates blog post |

## Product Catalog

| Tool | Description |
|------|-------------|
| `tenant_product_categories_create` | Creates product category |
| `tenant_product_categories_list` | Lists categories |
| `tenant_product_categories_tree` | Gets category tree |
| `tenant_product_categories_get` | Gets category |
| `tenant_product_categories_update` | Updates category |
| `tenant_product_attributes_create` | Creates product attribute |
| `tenant_product_attributes_list` | Lists attributes |
| `tenant_product_attributes_get` | Gets attribute |
| `tenant_product_attributes_update` | Updates attribute |
| `tenant_product_attribute_groups_create` | Creates attribute group |
| `tenant_product_attribute_groups_list` | Lists groups |
| `tenant_product_attribute_groups_get` | Gets group |
| `tenant_product_attribute_groups_update` | Updates group |
| `tenant_products_create` | Creates product |
| `tenant_products_list` | Lists products |
| `tenant_products_get` | Gets product |
| `tenant_products_update` | Updates product |

## Navigator (Menus)

| Tool | Description |
|------|-------------|
| `tenant_navigator_menus_list` | Lists menus |
| `tenant_navigator_menus_get` | Gets menu |
| `tenant_navigator_menus_create` | Creates menu |
| `tenant_navigator_menus_update` | Updates menu |

## Forms

| Tool | Description |
|------|-------------|
| `tenant_forms_create` | Creates form |
| `tenant_forms_list` | Lists forms |
| `tenant_forms_get` | Gets form |
| `tenant_forms_update` | Updates form |
| `tenant_forms_list_submissions` | Lists submissions |
| `tenant_forms_get_submission` | Gets submission |
| `tenant_forms_update_submission_status` | Updates submission status |

## Locations

| Tool | Description |
|------|-------------|
| `tenant_locations_create` | Creates location |
| `tenant_locations_list` | Lists locations |
| `tenant_locations_get` | Gets location |
| `tenant_locations_update` | Updates location |

## Media Manager

| Tool | Description |
|------|-------------|
| `tenant_media_upload` | Uploads file |
| `tenant_media_upload_optimized_image` | Uploads optimized image |
| `tenant_media_list` | Lists media |
| `tenant_media_get` | Gets media |
| `tenant_media_update_visibility` | Updates visibility |

## Site Settings

| Tool | Description |
|------|-------------|
| `tenant_site_settings_get` | Gets site settings |
| `tenant_site_settings_update` | Updates site settings |

## Translations

| Tool | Description |
|------|-------------|
| `tenant_translations_list` | Lists translations (filtered, paginated) |
| `tenant_translations_get` | Gets translation details |
| `tenant_translations_create` | Creates new translation |
| `tenant_translations_update` | Updates translation |
| `tenant_translations_bulk_export` | Exports all translations as JSON |
| `tenant_translations_bulk_import` | Imports translations from JSON |
| `tenant_translations_copy_from_language` | Copies translations from one language to another |
| `tenant_translations_stats` | Gets translation statistics |
| `tenant_translations_set_translation` | Sets single translation (upsert) |
| `tenant_translations_set_translation_multiple` | Sets translation in multiple languages |


## Public (Selected)

| Tool | Description |
|------|-------------|
| `public_popups_resolve` | Resolves active popups for a URL, optional language and page code |
| `public_locations_list` | Lists active public locations |
| `public_locations_get` | Gets active public location detail |
| `public_locations_geo_countries_list` | Lists active countries |
| `public_locations_geo_cities_list` | Lists active cities |
| `public_locations_geo_districts_list` | Lists active districts |

## Guardrails

- Frontend popup rendering should use `public_popups_resolve`, not tenant popup endpoints.
- Tenant popup tools are for content management only; public visibility must be derived from the public resolve surface.
