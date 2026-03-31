# Blog Module Reference

## What Is It Used For?

Editorial content management:
- Blog posts
- News
- Announcements
- Articles

## Components

### Categories
- Hierarchical structure (parent/child)
- Slug and name for each language

### Tags
- Flat structure
- Multiple tags per post

### Posts
- **Status**: `Draft`, `Published`, `Archived`
- **Publish Date**: Publication date
- **Cover Image**: Cover image
- **Multi-language support**

## MCP Tools

### Categories
```bash
tenant_blog_categories_create
tenant_blog_categories_list
tenant_blog_categories_get
tenant_blog_categories_update
```

### Tags
```bash
tenant_blog_tags_create
tenant_blog_tags_list
tenant_blog_tags_get
tenant_blog_tags_update
```

### Posts
```bash
tenant_blog_posts_create
tenant_blog_posts_list
tenant_blog_posts_get
tenant_blog_posts_update
```

## Public API

```bash
# List categories
GET /api/public/blog/categories

# List tags
GET /api/public/blog/tags

# List posts (paginated)
GET /api/public/blog/posts?page=1&pageSize=10

# Get post detail (by slug)
GET /api/public/blog/posts/{slug}
```

## Blog Post Example

```json
{
  "coverImageMediaFileId": "uuid-image",
  "status": "Published",
  "publishDate": "2026-04-01T10:00:00Z",
  "categoryIds": ["uuid-category"],
  "tagIds": ["uuid-tag-1", "uuid-tag-2"],
  "translations": [
    {
      "languageId": "uuid-en",
      "title": "Our First Blog Post",
      "content": "<p>Blog content...</p>",
      "slug": "our-first-blog-post",
      "metaTitle": "Our First Blog Post",
      "metaDescription": "This is our first blog post"
    }
  ]
}
```
