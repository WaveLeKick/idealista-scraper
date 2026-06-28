[Idealista Scraper](https://apify.com/makework36/idealista-scraper?fpr=data)

# Idealista Real Estate Scraper

> ⭐ **Useful?** [Leave a review](https://apify.com/makework36/idealista-scraper/reviews) — takes 10 seconds and helps a lot!

Scrape property listings from Idealista.com. Works with Spanish, Italian, and Portuguese markets. Extracts prices, locations, details, and images from search result pages.

## What data does it extract?

| Field | Description |
| --- | --- |
| title | Listing title (e.g., "Flat in calle de Alcalá") |
| price | Listed price (e.g., "€285,000") |
| details | Size, rooms, floor info (e.g., "3 bed, 2 bath, 95 m²") |
| location | Neighborhood or area |
| url | Direct link to the listing |
| image | Main listing photo URL |
| searchUrl | The search URL this listing came from |
| scrapedAt | ISO timestamp |

## Use cases

- **Property market research** — Track asking prices across neighborhoods or cities
- **Investment analysis** — Monitor listings in target areas to spot deals
- **Price comparison** — Compare prices per square meter across different zones
- **Real estate data feeds** — Build datasets for property analytics dashboards
- **Relocation research** — Quickly gather and compare available properties in a new city

## How to use

### Search for apartments in Madrid

```
{
    "searchUrls": [
        "https://www.idealista.com/en/venta-viviendas/madrid/"
    ],
    "maxListings": 50
}
```

### Multiple searches

```
{
    "searchUrls": [
        "https://www.idealista.com/en/venta-viviendas/barcelona/eixample/",
        "https://www.idealista.com/en/alquiler-viviendas/madrid/centro/",
        "https://www.idealista.com/en/venta-viviendas/valencia/"
    ],
    "maxListings": 100
}
```

### Rental listings in Lisbon

```
{
    "searchUrls": [
        "https://www.idealista.pt/arrendar-casas/lisboa/"
    ],
    "maxListings": 30
}
```

## Input parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| searchUrls | string[] | — | Idealista search result page URLs (required) |
| maxListings | integer | 50 | Maximum listings to extract (1-500) |

## Output example

```
{
    "title": "Flat in calle de Serrano, Salamanca, Madrid",
    "price": "€485,000",
    "details": "3 bed · 2 bath · 110 m² · 4th floor with lift",
    "location": "Salamanca, Madrid",
    "url": "https://www.idealista.com/inmueble/12345678/",
    "image": "https://img3.idealista.com/blur/WEB_LISTING/0/id.pro.es/12345678_xxl.jpg",
    "searchUrl": "https://www.idealista.com/en/venta-viviendas/madrid/barrio-de-salamanca/",
    "scrapedAt": "2025-03-22T18:06:12.000Z"
}
```

## Performance & cost

- Uses residential proxies geolocated in Spain to avoid blocks
- Handles Idealista's cookie consent popup automatically
- Falls back to JSON-LD structured data if DOM selectors fail
- Retries up to 5 times per URL with different proxy sessions

## FAQ

**How do I get the search URLs?**
Go to idealista.com (or idealista.pt / idealista.it), set your filters (location, price range, bedrooms, etc.), and copy the URL from your browser. The scraper works with whatever filters you apply on the site.

**Does it scrape individual listing detail pages?**
No — it extracts data from search result pages only. Each listing includes a direct URL you can use to visit the full detail page.

**Why does Idealista block requests?**
Idealista has aggressive anti-scraping measures. The actor uses stealth browser settings and residential proxies to work around this, but some requests may still fail. Running with a lower `maxListings` value and from Spanish IPs gives the best results.

**Does it work with Idealista Italy and Portugal?**
Yes. Use the appropriate domain: idealista.it for Italy, idealista.pt for Portugal. The scraper extracts the same fields regardless of the country.

## ❓ Extended FAQ

### How much does it cost to scrape Idealista?

Pay-per-result on Apify (no monthly subscription). At $1.00 per 1,000 listings, scraping 100 properties costs ~$0.10. Apify Free plan includes $5 credit (~5,000 listings to start).

### Is Idealista scraping legal in Spain?

Idealista listings are public data. Scraping for personal market research, lead generation, or analytics is generally legal under EU GDPR when the data is non-personal. Always respect Idealista's Terms of Service and don't republish copyrighted content.

### Can I get historical Idealista price data?

The scraper returns current listings only. To track price history, schedule the scraper to run daily or weekly (Apify supports cron schedules) and store results.

### Which Idealista markets are supported?

Idealista España (.com), Italia (.it), and Portugal (.pt) — all three countries Idealista operates in. Pass URLs from any domain.

### Can I filter by price range, rooms, or property type?

Yes — apply the filters directly on idealista.com / .it / .pt before copying the URL. The scraper respects all filter parameters in the URL.

### What's the difference vs other Idealista scrapers?

HTTP + light browser fallback (no full Puppeteer overhead). 5-10× cheaper compute than browser-only competitors. Built-in residential proxy + retries to handle Idealista's anti-bot measures.

## 🔗 Other scrapers by makework36

- [VRBO Scraper](https://apify.com/makework36/vrbo-scraper) — vacation rentals + Expedia hotels
- [Trustpilot Scraper API](https://apify.com/makework36/trustpilot-reviews-scraper) — reviews & business search
- [Fast Airbnb Price Scraper](https://apify.com/makework36/fast-airbnb-price-scraper) — Airbnb listings + prices
- [Flight Price Scraper 2026](https://apify.com/makework36/flight-price-scraper) — compare flights across 7 sources