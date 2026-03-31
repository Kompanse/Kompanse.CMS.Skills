# Translations Module Reference

## What Is It Used For?

Managing UI strings and text translations:
- Button texts
- Labels
- Error messages
- Notification texts
- Footer texts

## Key Concepts

- **Key**: Unique translation key (e.g., `home.hero.title`)
- **Value**: Translation value
- **Language**: Separate record for each language

## MCP Tools

```bash
# List translations
tenant_translations_list

# Get translation detail
tenant_translations_get

# Create new translation
tenant_translations_update

# Update translation
tenant_translations_update

# Bulk export
tenant_translations_bulk_export

# Bulk import
tenant_translations_bulk_import

# Copy from one language to another
tenant_translations_copy_from_language

# Statistics
tenant_translations_stats

# Set single translation (upsert)
tenant_translations_set_translation

# Set translation in multiple languages
tenant_translations_set_translation_multiple
```

## Public API

```bash
# Translations in specific language
GET /api/public/translations/{languageCode}

# Translations in all languages
GET /api/public/translations
```

## Creating Translation

### Single Language
```json
{
  "languageId": "uuid-en",
  "key": "home.hero.title",
  "value": "Welcome"
}
```

### Multiple Languages (At Once)
```json
{
  "key": "home.hero.title",
  "translations": {
    "en": "Welcome",
    "tr": "Hoş Geldiniz",
    "de": "Willkommen"
  }
}
```

## Bulk Import Example

```json
{
  "translations": {
    "home.title": {
      "en": "Home Page",
      "tr": "Ana Sayfa"
    },
    "home.subtitle": {
      "en": "Welcome to our site",
      "tr": "Sitemize hoş geldiniz"
    },
    "contact.email": {
      "en": "info@example.com",
      "tr": "info@example.com"
    }
  }
}
```

## Copy From Language

```json
{
  "sourceLanguageId": "uuid-en",
  "targetLanguageId": "uuid-tr",
  "overwriteExisting": false
}
```

## Frontend Integration

```typescript
// Get all translations
const allTranslations = await fetch('/api/public/translations', {
  headers: { 'X-Api-Key': apiKey }
}).then(r => r.json());

// Get only EN translations
const enTranslations = await fetch('/api/public/translations/en', {
  headers: { 'X-Api-Key': apiKey }
}).then(r => r.json());
```

## Statistics Response

```json
{
  "totalTranslations": 150,
  "totalUniqueKeys": 50,
  "languages": [
    {
      "languageCode": "en",
      "languageName": "English",
      "translationCount": 50,
      "percentage": 100
    },
    {
      "languageCode": "tr",
      "languageName": "Türkçe",
      "translationCount": 45,
      "percentage": 90
    }
  ]
}
```
