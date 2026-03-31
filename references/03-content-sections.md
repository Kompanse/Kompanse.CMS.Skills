# Content Sections Detailed Guide

## What Is It Used For?

Managing structured blocks within pages:
- Hero areas
- Feature cards
- Icon feature lists
- Numeric statistic blocks
- Reference logos
- FAQ sections
- Customer testimonials
- CTA banners
- Rich text blocks
- Image + text blocks

## Pages vs Content Sections

| Feature | Pages | Content Sections |
|---------|-------|------------------|
| Full page management | ✅ | ❌ |
| Page block management | ❌ | ✅ |
| URL/Slug support | ✅ | ❌ |
| Template-based component | ❌ | ✅ |
| Repeating card structures | ❌ | ✅ |

## Template Structure

### Single Section (No Items)

| Template Code | Description |
|---------------|-------------|
| `hero-basic` | Basic hero area |
| `hero-split` | Two-column hero |
| `hero-centered` | Centered hero |
| `cta-banner` | Single action call area |
| `rich-text-block` | Free text block |
| `media-text` | Image + text combination |
| `contact-info` | Contact information block |
| `before-after` | Before/after comparison |
| `video-block` | Video player block |
| `footer-brand` | Footer brand area |

### Item-Based Section (Repeating Records)

| Template Code | itemListCode | Description |
|---------------|--------------|-------------|
| `feature-cards` | `cards` | Feature cards |
| `icon-features` | `features` | Icon feature list |
| `stats-grid` | `stats` | Statistics numbers |
| `logo-cloud` | `logos` | Reference logos |
| `faq-list` | `questions` | Frequently asked questions |
| `testimonial-list` | `testimonials` | Customer testimonials |
| `timeline` | `events` | Timeline |
| `process-steps` | `steps` | Process steps |
| `team-grid` | `members` | Team members |
| `branch-list` | `branches` | Branch/location list |
| `download-list` | `downloads` | Downloadable files |
| `pricing-cards` | `plans` | Pricing cards |
| `comparison-table` | `rows` | Comparison table |
| `product-highlights` | `products` | Product highlights |
| `product-specs` | `specs` | Technical specifications |
| `gallery-grid` | `images` | Gallery images |
| `footer-links` | `links` | Footer link groups |
| `social-links` | `links` | Social media links |
| `legal-links` | `links` | Legal links |

## MCP Tools

```bash
# List available templates
tenant_content_sections_templates_list

# Get template details
tenant_content_sections_templates_get_by_code

# Create new section
tenant_content_sections_create

# List sections
tenant_content_sections_list

# Get section by code
tenant_content_sections_get_by_code

# Update section
tenant_content_sections_update
```

## Public API Usage

```bash
# Fetch single section
GET /api/public/content-sections/by-key/{code}

# Fetch multiple sections
POST /api/public/content-sections/by-keys
```

## Section Creation Example

```json
{
  "body": {
    "code": "home-hero",
    "templateCode": "hero-basic",
    "isActive": true,
    "translations": [
      {
        "languageCode": "en",
        "fields": {
          "eyebrow": "Welcome",
          "title": "The Best Solutions for Your Company",
          "subtitle": "We are here with our 10 years of experience",
          "ctaPrimaryLabel": "Contact Us",
          "ctaPrimaryUrl": "/contact"
        }
      }
    ]
  }
}
```

## Scenario-Based Template Selection

**Corporate Website**
- Hero: `hero-split` or `hero-basic`
- Features: `feature-cards` or `icon-features`
- Stats: `stats-grid`
- References: `logo-cloud`, `testimonial-list`
- Team: `team-grid`
- Contact: `contact-info`
- CTA: `cta-banner`
- Footer: `footer-brand`, `footer-links`, `social-links`

**Landing Page**
- Hero: `hero-centered` or `hero-basic`
- Features: `feature-cards`
- Benefits: `icon-features`
- Stats: `stats-grid`
- Testimonials: `testimonial-list`
- FAQ: `faq-list`
- CTA: `cta-banner`

**E-commerce / Product Site**
- Hero: `hero-basic`
- Featured products: `product-highlights`
- Features: `product-specs`
- Pricing: `pricing-cards` or `comparison-table`
- References: `testimonial-list`
