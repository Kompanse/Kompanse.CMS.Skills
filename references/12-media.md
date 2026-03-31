# Media Manager Module Reference

## What Is It Used For?

File management:
- Images (jpg, png, webp, svg)
- Videos
- Documents (PDF, docx)
- Other files

## Features

- **isPublic**: Is it publicly accessible?
- **fileCategory**: File category (Image, Video, Document, Other)
- **Optimized Images**: Automatic WebP optimization
- **CDN**: Served via global CDN

## MCP Tools

```bash
# Upload file (standard)
tenant_media_upload

# Upload optimized image
tenant_media_upload_optimized_image

# List files
tenant_media_list

# Get file detail
tenant_media_get

# Update visibility
tenant_media_update_visibility
```

## Public Access

```bash
# Direct access to public files (X-Api-Key not required)
GET /media/{customerSlug}/{fileName}
```

## Usage Examples

### Image Upload
```bash
tenant_media_upload
# filePath: "/path/to/image.jpg"
# fileName: "hero-banner.jpg"  # optional
# contentType: "image/jpeg"    # optional
```

### Optimized Image
```bash
tenant_media_upload_optimized_image
# filePath: "/path/to/photo.jpg"
# Automatic WebP conversion is performed
```

### Visibility Settings
```bash
tenant_media_update_visibility
# id: "uuid-file"
# body: { "isPublic": true }
```

## Frontend Integration

```html
<!-- Public image -->
<img src="/media/mysite/filename.webp" alt="Description" />

<!-- With full URL -->
<img src="https://api.example.com/media/mysite/filename.webp" alt="Description" />
```

## Notes

- Upload files to Media Manager first
- Use the `mediaFileId` value in other modules
- Public files are served directly via CDN
- X-Api-Key is only required for tenant management, not for public media
