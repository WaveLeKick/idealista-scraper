[Idealista Scraper](https://apify.com/gio21/idealista-scraper?fpr=data)

# Idealista Scraper 🏠

Scrape property listings from **Idealista** — the #1 real-estate portal in Spain 🇪🇸, Portugal 🇵🇹 and Italy 🇮🇹.

## What it does

Search listings by city + operation (rent/sale) and extract structured property data:

- **Title**, **price**, **price per m²**
- **Location** (city, neighborhood, address hint)
- **Area** in m², **rooms**, **bathrooms**, **floor**
- **Property type** (apartment, house, studio, country house…)
- **Condition** and **energy certificate**
- **Features** (terrace, parking, lift, pool, AC, furnished…)
- **Images**, **agency** / owner, phone (when exposed)
- **Listing URL** and **listing ID**
- **Published / updated** date
- **Coordinates** (when available)

## Why this scraper?

Idealista dominates Iberia + Italy but is underserved on Apify Store. This is a focused, production-grade scraper:

- 🌐 Multi-country: `idealista.com` (ES), `idealista.pt` (PT), `idealista.it` (IT)
- 🏡 Rent + Sale + Vacation + Shared rooms
- 🗺️ City or custom URL input
- 💰 Transparent PPE pricing

## Input

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `country` | string | `es` | `es`, `pt`, or `it` |
| `operation` | string | `venta` | `venta`/`sale`, `alquiler`/`rent`, `habitacion`/`room`, `vacacional`/`vacation` |
| `city` | string | `madrid` | City slug (e.g. `madrid`, `lisboa`, `milano`) |
| `startUrl` | string | — | Optional: direct search URL (overrides country/operation/city) |
| `maxItems` | integer | `50` | Max listings to return |
| `maxPages` | integer | `5` | Max search pages (~30 listings/page) |

## Output

```
{
  "listingId": "106789123",
  "title": "Piso en venta en Calle de Serrano",
  "operation": "venta",
  "propertyType": "Piso",
  "price": 695000,
  "currency": "EUR",
  "pricePerSqm": 7722,
  "area": 90,
  "rooms": 2,
  "bathrooms": 2,
  "floor": "3ª exterior con ascensor",
  "city": "Madrid",
  "neighborhood": "Salamanca",
  "addressHint": "Calle de Serrano",
  "description": "Exclusivo piso reformado con vistas...",
  "features": ["Terraza", "Aire acondicionado", "Amueblado", "Ascensor"],
  "condition": "Buen estado",
  "energyCertificate": "D",
  "agency": "Inmobiliaria XYZ",
  "phone": "+34 912 345 678",
  "images": ["https://img4.idealista.com/..."],
  "latitude": 40.4258,
  "longitude": -3.6866,
  "publishedAt": "2026-03-15",
  "url": "https://www.idealista.com/inmueble/106789123/"
}
```

## Pricing

Pay-per-event: **$0.005 per listing** ($5 per 1,000 listings).

Free users: up to 15 listings per run.

## Use cases

- **PropTech / real-estate SaaS** — Supply feeds for rental platforms, CRMs, price-comparison tools
- **Investment research** — Yield analysis, market density, price-per-m² trends
- **Relocation services** — Build offer shortlists for clients moving to Iberia / Italy
- **Competitive intel** — Track agency market share by neighborhood
- **Price history** — Daily runs to detect drops and new listings