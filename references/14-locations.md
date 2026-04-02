# Locations Module

Locations module manages branch/store/service-point style location records.

## Data Shape

- `countryId`, `cityId`, `districtId`: Admin-managed geo reference IDs (Base DB)
- `address`, `groupName`, `latitude`, `longitude`
- `email`, `phone`, `googleMapsLink`
- `isActive`
- translations: `title`, `name`

## Tenant Tools (MCP)

| Tool | Description |
|------|-------------|
| `tenant_locations_create` | Creates location |
| `tenant_locations_list` | Lists locations (filtered, paginated) |
| `tenant_locations_get` | Gets location detail |
| `tenant_locations_update` | Updates location |

## Public Tools (MCP)

| Tool | Description |
|------|-------------|
| `public_locations_list` | Lists active public locations |
| `public_locations_get` | Gets active public location detail |
| `public_locations_geo_countries_list` | Lists active countries |
| `public_locations_geo_cities_list` | Lists active cities |
| `public_locations_geo_districts_list` | Lists active districts |

## Public API Endpoints

| Endpoint | Description | Query Parameters |
|----------|-------------|------------------|
| `GET /api/public/locations` | Lists active locations | `page`, `pageSize`, `search`, `groupName`, `countryId`, `cityId`, `districtId`, `lang` |
| `GET /api/public/locations/{id}` | Gets active location detail | `lang` |
| `GET /api/public/locations/geo/countries` | Lists active countries | - |
| `GET /api/public/locations/geo/cities` | Lists active cities | `countryId` |
| `GET /api/public/locations/geo/districts` | Lists active districts | `cityId` |

## Typical Workflow

1. Read active modules with `tenant_modules_list` and confirm `locations` exists.
2. If needed, create records with `tenant_locations_create`.
3. Verify with `public_locations_list` and `public_locations_get`.
4. Render in frontend from `/api/public/locations`.

## Notes

- `countryId/cityId/districtId` values are validated by backend hierarchy rules.
- Public endpoints only return active locations.
- `lang` controls translated `title`/`name` selection.
