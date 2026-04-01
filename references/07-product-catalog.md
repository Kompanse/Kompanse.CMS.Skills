# Product Catalog Module Reference

## What Is It Used For?

Product management:
- Product lists
- Categories (hierarchical)
- Product attributes (filtering)
- Pricing

## Components

### Categories
- Hierarchical tree structure
- Slug, name, description for each language
- Cover image support

### Attribute Groups
- Grouping attributes
- Example: "Technical Specifications", "General Features"

### Attribute Definitions
- **Data Type**: `Text`, `Number`, `Decimal`, `Boolean`, `Date`, `Select`
- **isFilterable**: Show in filter panel?
- **isSortable**: Allow sorting?
- **Unit**: Unit (kg, cm, etc.)
- **Options**: Options for Select type

### Products
- **Code**: Unique code (like SKU)
- **Status**: `Draft`, `Published`, `Archived`
- Cover image + gallery images
- Attribute values
- Multiple category support

## MCP Tools

### Categories
```bash
tenant_product_categories_create
tenant_product_categories_list
tenant_product_categories_tree
tenant_product_categories_get
tenant_product_categories_update
```

### Attribute Groups
```bash
tenant_product_attribute_groups_create
tenant_product_attribute_groups_list
tenant_product_attribute_groups_get
tenant_product_attribute_groups_update
```

### Attributes
```bash
tenant_product_attributes_create
tenant_product_attributes_list
tenant_product_attributes_get
tenant_product_attributes_update
tenant_product_attributes_add_option
tenant_product_attributes_update_option
```

### Products
```bash
tenant_products_create
tenant_products_list
tenant_products_get
tenant_products_update
```

## Public API

```bash
# Category tree
GET /api/public/product-catalog/categories

# Product list (filtered)
GET /api/public/product-catalog/products?categoryId=xxx&search=product&lang=en

# Product detail
GET /api/public/product-catalog/products/{slug}

# Filter definitions
GET /api/public/product-catalog/products/filters
```

## Product Creation Example

```json
{
  "code": "iphone-16-pro",
  "sku": "IP16PRO-256-BLK",
  "status": "Published",
  "coverImageMediaFileId": "uuid-cover",
  "categoryIds": ["uuid-phones"],
  "translations": [
    {
      "languageId": "uuid-en",
      "name": "iPhone 16 Pro",
      "slug": "iphone-16-pro",
      "shortDescription": "Apple iPhone 16 Pro 256GB",
      "description": "<p>Detailed description...</p>",
      "metaTitle": "iPhone 16 Pro | Store",
      "metaDescription": "iPhone 16 Pro at the best price"
    }
  ],
  "images": [
    { "mediaFileId": "uuid-1", "sortOrder": 1, "altText": "Front view" },
    { "mediaFileId": "uuid-2", "sortOrder": 2, "altText": "Back view" }
  ],
  "attributeValues": [
    {
      "attributeDefinitionId": "uuid-color",
      "attributeOptionId": "uuid-black"
    },
    {
      "attributeDefinitionId": "uuid-weight",
      "decimalValue": 0.199,
      "unit": "kg"
    }
  ]
}
```

## Filtering Example

```bash
# Select type filter
GET /api/public/product-catalog/products?attrs[color]=Black

# Multi-select on the same attribute (OR)
GET /api/public/product-catalog/products?attrs[brand]=Veda&attrs[brand]=Apicenna&attrs[brand]=GigiVet

# Decimal range filter
GET /api/public/product-catalog/products?attrs[weight_min]=0.1&attrs[weight_max]=0.5

# Boolean filter
GET /api/public/product-catalog/products?attrs[warranty]=true

# Multiple filters
GET /api/public/product-catalog/products?categoryId=xxx&attrs[color]=Blue&attrs[price_max]=5000
```

Filtering semantics:
- Repeated values of the same `attrs[code]` key are combined with `OR`.
- Different attribute keys are combined with `AND`.

Example:
`attrs[brand]=Veda&attrs[brand]=Apicenna&attrs[form]=Tablet&attrs[form]=Powder`
means `(brand IN [Veda, Apicenna]) AND (form IN [Tablet, Powder])`.
