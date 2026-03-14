# country-flag

Country metadata datasets with dial codes, phone length rules, and flag image paths for local assets or CDN usage.

## What this project contains

This folder provides:

- a local dataset that points to bundled flag PNG files
- a CDN dataset for `flagcdn.com`
- a CDN dataset for `addevin.github.io`
- a local `country-flag/` image directory containing country flag PNGs

## Project structure

```text
country-flag/
├─ countries-local.json
├─ countries-cdn1.json
├─ countries-cdn2.json
├─ country-flag/
│  ├─ ad.png
│  ├─ ae.png
│  ├─ af.png
│  └─ ...
└─ README.md
```

## Dataset files

### `countries-local.json`

Uses local flag image paths.

Example:

```json
{
  "name": "United States",
  "dial_code": "+1",
  "code": "US",
  "flag_url": "country-flag/us.png",
  "length": {
    "min": 10,
    "max": 10
  }
}
```

### `countries-cdn1.json`

Uses `flagcdn.com` image URLs.

URL pattern:

```text
https://flagcdn.com/w320/us.png
```

Example:

```json
{
  "name": "United States",
  "dial_code": "+1",
  "code": "US",
  "flag_url": "https://flagcdn.com/w320/us.png",
  "length": {
    "min": 10,
    "max": 10
  }
}
```

### `countries-cdn2.json`

Uses `addevin.github.io` image URLs.

URL pattern:

```text
https://addevin.github.io/country-list-json/country-flag/us.png
```

Example:

```json
{
  "name": "United States",
  "dial_code": "+1",
  "code": "US",
  "flag_url": "https://addevin.github.io/country-list-json/country-flag/us.png",
  "length": {
    "min": 10,
    "max": 10
  }
}
```

## Data shape

Each country item includes:

- `name` - country name
- `dial_code` - international calling code
- `code` - 2-letter country code
- `flag_url` - local image path or remote image URL
- `length.min` - minimum phone number length
- `length.max` - maximum phone number length

## Local asset folder

### `country-flag/`

Contains local PNG flag assets keyed by lowercase country code.

Examples:

- `country-flag/us.png`
- `country-flag/in.png`
- `country-flag/gb.png`

## Which file should you use?

Choose based on where you want the flag images to load from:

### `countries-local.json`

Use this if your app will use the local PNG files included in this repository.

- you want bundled local assets
- you want to avoid external image requests
- you need predictable offline or self-hosted behavior

### `countries-cdn1.json`

Use this if your app should load flags from FlagCDN.

- you want `https://flagcdn.com/w320/<code>.png`
- you do not want to bundle local image files

### `countries-cdn2.json`

Use this if your app should load flags from the GitHub Pages CDN version.

- you want `https://addevin.github.io/country-list-json/country-flag/<code>.png`
- you do not want to bundle local image files

## Notes

- The local image folder is named `country-flag/` inside the project root.
- Country records include phone length rules, useful for form validation and country pickers.

## Typical usage example

```js
import countries from './countries-local.json';

const india = countries.find((item) => item.code === 'US');

console.log(india.name);
console.log(india.dial_code);
console.log(india.flag_url);
console.log(india.length.min, india.length.max);
```

## Summary

This project is a reusable country data pack for apps that need:

- country names
- dial codes
- flag images
- phone number length metadata

## View all flags

<a href="https://addevin.github.io/country-list-json/" target="_blank" rel="noopener noreferrer">View all the flags</a>
