# Forms Module Reference

## What Is It Used For?

Data collection:
- Contact forms
- Quote forms
- Application forms
- Surveys

## Features

- **Code**: Unique identifier
- **isPublic**: Is public submit enabled?
- **Form Fields**: Not predefined in CMS, sent as name/value from frontend
- **Submission**: Each form submission is saved separately
- **Status**: `New`, `Read`, `Archived`, `Spam`

## MCP Tools

```bash
# Create form
tenant_forms_create

# List forms
tenant_forms_list

# Get form detail
tenant_forms_get

# Update form
tenant_forms_update

# List submissions
tenant_forms_list_submissions

# Get submission detail
tenant_forms_get_submission

# Update submission status
tenant_forms_update_submission_status
```

## Public API

```bash
# Form submission
POST /api/public/forms/{code}/submit
```

## Form Submission Example

```json
{
  "fields": [
    { "name": "name", "value": "John Doe" },
    { "name": "email", "value": "john@example.com" },
    { "name": "phone", "value": "+1 555 000 00 00" },
    { "name": "message", "value": "I want to get information" }
  ],
  "sourceUrl": "https://example.com/contact",
  "referrer": "https://google.com"
}
```

## Response

```json
{
  "success": true,
  "data": {
    "submissionId": "uuid",
    "status": "New",
    "submittedAt": "2026-03-28T14:15:00Z"
  }
}
```

## Notes

- Form fields are not predefined in CMS
- `name` value comes from frontend
- Multiple values can be sent for the same `name`
- IP address and UserAgent are automatically saved
