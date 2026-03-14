# country-flag

Country metadata dataset with flag image references and local flag assets.

## What this project contains

This folder provides:

- a country list with dial codes and phone number length rules
- a version that points to remote flag CDN URLs
- a version that points to local flag image files
- a local `country-flag/` image directory containing country flag PNGs

## Project structure

```text
country-flag/
├─ countries.json
├─ countries-local.json
├─ country-flag/
│  ├─ ad.png
│  ├─ ae.png
│  ├─ af.png
│  └─ ...
└─ README.md
```

## Files

### `countries.json`

Primary dataset using remote flag image URLs.

Each item includes:

- `name` - country name
- `dial_code` - international calling code
- `code` - ISO-style 2-letter country code
- `flage_url` - remote image URL
- `length.min` - minimum phone number length
- `length.max` - maximum phone number length

Example:

```json
{
  "name": "United States",
  "dial_code": "+1",
  "code": "US",
  "flage_url": "https://flagcdn.com/w320/us.png",
  "length": {
    "min": 10,
    "max": 10
  }
}
```

### `countries-local.json`

Same country dataset, but `flage_url` values point to local files instead of external CDN URLs.

Example:

```json
{
  "name": "United States",
  "dial_code": "+1",
  "code": "US",
  "flage_url": "country-flag/us.png",
  "length": {
    "min": 10,
    "max": 10
  }
}
```

### `country-flag/`

Local PNG flag assets keyed by country code in lowercase.

Examples:

- `country-flag/us.png`
- `country-flag/in.png`
- `country-flag/gb.png`

## Use cases

- country selector dropdowns
- phone number input components
- signup forms with country code picker
- offline/local flag rendering
- replacing remote flag URLs with local assets

## Local vs remote dataset

Use `countries.json` when:

- you want to load flags from CDN
- you do not want to store image assets in your app

Use `countries-local.json` when:

- you want local image files
- you need more predictable asset delivery
- you want to avoid runtime dependency on external image URLs

## Notes

- The property name is `flage_url`, not `flag_url`.
- The local image folder is named `country-flag/` inside the project root.
- Country records also include phone length rules, which are useful for input validation.

## Typical integration example

```js
import countries from './countries-local.json';

const india = countries.find((item) => item.code === 'IN');

console.log(india.name);
console.log(india.dial_code);
console.log(india.flage_url);
console.log(india.length.min, india.length.max);
```

## Summary

This project is a reusable country data pack for apps that need:

- country names
- dial codes
- flag images
- phone number length metadata
