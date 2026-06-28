[Idealista Scraper](https://apify.com/burbn/idealista-scraper?fpr=data)

# Idealista Properties Scraper | Idealista Real Estate Data API

Search Idealista properties for rent or sale. Extract Idealista real estate data including property prices, addresses, sizes, rooms, floor plans, contact info, photos, videos, GPS coordinates, amenities, and more across Italy, Spain, and Portugal. The best Idealista property scraper for real estate research, market analysis, and property intelligence.

## ❓ What is Idealista Properties Scraper?

**Idealista Properties Scraper** is a powerful Apify actor that lets you search and extract property listing data from **Idealista** — the largest real estate marketplace in Southern Europe. Whether you want to find rental apartments, compare property prices, monitor real estate markets, or collect property data for investment research — this Idealista property scraper does it all automatically.

With this Idealista properties search tool, you can:

- 🔍 **Search Idealista properties by location** — Search any city, neighborhood, or area across Italy, Spain, and Portugal
- 🏠 **Extract for rent or sale** — Get rental listings or properties for sale with a single toggle
- 💰 **Get complete pricing data** — Extract prices, price per sqm, price drops, and currency info
- 🏢 **Get full property details** — Extract size, rooms, bathrooms, floor, address, GPS coordinates, description, and status
- 📸 **Get all media** — Extract property thumbnails, all listing images, and video URLs
- 📞 **Get contact information** — Extract agent name, agency, phone number, and contact method
- 🎛️ **40+ advanced filters** — Filter by price, size, bedrooms, amenities, property type, and more
- 📄 **Auto-pagination** — Automatically fetches all pages of results with smart rate limiting
- 📊 **Export structured data** — Download results in JSON, CSV, Excel, XML, and RSS formats

## 🎯 What Data Can You Extract from Idealista Properties?

This Idealista property scraper extracts the following data for each listing:

| Field | Description |
| --- | --- |
| `propertyCode` | Unique Idealista property identifier |
| `title` | Property listing title |
| `description` | Full property description |
| `price` | Property price (rent per month or sale price) |
| `currencySuffix` | Currency and period (e.g., €/month) |
| `priceByArea` | Price per square meter |
| `formerPrice` | Previous price (if price dropped) |
| `priceDropPercentage` | Price drop percentage |
| `propertyType` | Property type (studio, flat, house, etc.) |
| `operation` | Operation type (rent or sale) |
| `size` | Property size in square meters |
| `rooms` | Number of rooms |
| `bathrooms` | Number of bathrooms |
| `floor` | Floor number |
| `address` | Full property address |
| `province` | Province name |
| `municipality` | City/municipality name |
| `district` | District name |
| `neighborhood` | Neighborhood name |
| `country` | Country code (it, es, pt) |
| `latitude` | GPS latitude coordinate |
| `longitude` | GPS longitude coordinate |
| `url` | Direct link to Idealista property page |
| `thumbnail` | Property thumbnail image URL |
| `images` | All property listing image URLs |
| `videos` | Property video URLs |
| `numPhotos` | Total number of photos |
| `contactName` | Agent/owner contact name |
| `commercialName` | Agency commercial name |
| `phoneNumber` | Contact phone number |
| `userType` | Contact type (professional or private) |
| `hasLift` | Whether property has an elevator |
| `hasSwimmingPool` | Whether property has a swimming pool |
| `hasTerrace` | Whether property has a terrace |
| `hasAirConditioning` | Whether property has air conditioning |
| `hasGarden` | Whether property has a garden |
| `hasBoxRoom` | Whether property has a box/storage room |

## 📍 How to Get Idealista Location IDs

Before using this Idealista property scraper, you need a **location ID**. Get it using our companion actor:

👉 **[Idealista Auto-Complete](https://apify.com/burbn/idealista-auto-complete)** — Search for any city, neighborhood, or area and get the location ID instantly.

**Example Idealista location IDs:**

| Location | Location ID |
| --- | --- |
| Milano, Italy | `0-EU-IT-MI-01-001-135` |
| Roma, Italy | `0-EU-IT-RM-01-001-088` |
| Madrid, Spain | `0-EU-ES-28-07-001-079` |
| Barcelona, Spain | `0-EU-ES-08-07-001-019` |
| Lisbon, Portugal | `0-EU-PT-11-01-001-000` |

## 🚀 How to Use Idealista Properties Scraper

### Step 1: Get Your Location ID

Use the **[Idealista Auto-Complete](https://apify.com/burbn/idealista-auto-complete)** actor to search for a city or area and get its location ID.

### Step 2: Configure Your Search

| Input | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `locationId` | String | ✅ Yes | `0-EU-IT-MI-01-001-135` | Idealista location ID from Auto-Complete |
| `operation` | String | ✅ Yes | `rent` | `rent` or `sale` |
| `country` | String | ❌ No | `it` | Country: `it`, `es`, `pt` |
| `propertyType` | String | ❌ No | All | `homes`, `bedrooms`, `offices`, `premises`, etc. |
| `sort` | String | ❌ No | `asc` | Sort by price: `asc` or `desc` |
| `locale` | String | ❌ No | `en` | Language for descriptions |
| `maxItems` | Number | ❌ No | `40` | Results per API page (max 40) |
| `maxPages` | Number | ❌ No | `0` | Max pages to scrape (0 = all) |
| `minPrice` | Number | ❌ No | `0` | Minimum price filter |
| `maxPrice` | Number | ❌ No | `0` | Maximum price filter |
| `minSize` | Number | ❌ No | `0` | Minimum size in sqm |
| `maxSize` | Number | ❌ No | `0` | Maximum size in sqm |
| `bedrooms` | String | ❌ No | Any | `0`, `1`, `2`, `3`, `4` |
| `bathrooms` | String | ❌ No | Any | `1`, `2`, `3` |

### Step 3: Run and Download Results

Click **Start** to run the Idealista property scraper. Results are available in JSON, CSV, Excel, XML, and RSS formats.

## 📋 Example Input

```
{
  "locationId": "0-EU-IT-MI-01-001-135",
  "operation": "rent",
  "country": "it",
  "sort": "asc",
  "locale": "en",
  "maxItems": 40,
  "maxPages": 1,
  "maxPrice": 1000,
  "bedrooms": "2",
  "airConditioning": true
}
```

## 📋 Example Output

```
{
  "propertyCode": "35524940",
  "title": "Flat in via Privata Filippo Tommaso Marinetti",
  "subtitle": "Turro, Milano",
  "description": "Studio apartment available immediately, furnished...",
  "price": 400,
  "currencySuffix": "€/month",
  "priceByArea": 16,
  "propertyType": "studio",
  "operation": "rent",
  "size": 25,
  "rooms": 1,
  "bathrooms": 1,
  "floor": "5",
  "address": "via Privata Filippo Tommaso Marinetti",
  "province": "Milano",
  "municipality": "Milano",
  "district": "Greco - Turro",
  "neighborhood": "Turro",
  "country": "it",
  "latitude": 45.4972051,
  "longitude": 9.2285924,
  "url": "https://www.idealista.it/immobile/35524940/",
  "thumbnail": "https://img4.idealista.it/...",
  "images": ["https://img4.idealista.it/..."],
  "videos": [],
  "numPhotos": 7,
  "hasLift": true,
  "hasSwimmingPool": false,
  "hasTerrace": false,
  "hasAirConditioning": false,
  "contactName": "LA CASA IN 24H DI STEFANO CECCONELLO",
  "commercialName": "LA CASA IN 24H DI STEFANO CECCONELLO",
  "phoneNumber": "0289735826",
  "userType": "professional"
}
```

## 🎨 Dataset Views

The Idealista property scraper provides 3 organized dataset views for easy analysis:

| View | Description |
| --- | --- |
| 📊 **Properties Overview** | Property code, thumbnail, title, price, type, size, rooms, address, images, videos, URL |
| 📋 **Property Details** | Full details with coordinates, description, status, features, amenities, media |
| 📞 **Contact Information** | Agent name, agency, phone number, contact type, and method |

## 🎛️ Advanced Filters

This Idealista scraper supports 40+ filters to narrow your property search:

| Filter | Type | Values |
| --- | --- | --- |
| `swimmingPool` | Boolean | Swimming pool |
| `airConditioning` | Boolean | Air conditioning |
| `elevator` | Boolean | Elevator/lift |
| `terrace` | Boolean | Terrace |
| `garden` | Boolean | Garden |
| `garage` | Boolean | Garage/parking |
| `penthouse` | Boolean | Penthouse properties |
| `duplex` | Boolean | Duplex properties |
| `luxury` | Boolean | Luxury properties |
| `seaViews` | Boolean | Sea view properties |
| `exterior` | Boolean | Exterior-facing properties |
| `virtualTour` | Boolean | Virtual tour available |
| `storeRoom` | Boolean | Storage room |
| `builtinWardrobes` | Boolean | Built-in wardrobes |
| `accessible` | Boolean | Wheelchair accessible |
| `privateOwner` | Boolean | Private owner listings |
| `furnished` | String | `furnished` or `furnishedKitchen` |
| `preservations` | String | `renew`, `newDevelopment`, `good` |
| `sinceDate` | String | `T` (48h), `W` (week), `M` (month) |
| `rentalUsages` | String | `seasonal` or `longTerm` |
| `smokingPolicy` | String | `allowed` or `disallowed` |
| `petsPolicy` | String | `allowed` or `disallowed` |

## 💡 Use Cases for Idealista Properties Scraper

- **Real Estate Research** — Search and compare rental or sale property prices across cities and neighborhoods
- **Market Analysis** — Monitor property price trends, price drops, and new listings in target areas
- **Investment Research** — Analyze property prices per sqm, rental yields, and market supply
- **Relocation Planning** — Find apartments or houses matching your budget, size, and amenity requirements
- **Lead Generation** — Extract agent and agency contact details for real estate business outreach
- **Property Monitoring** — Track new listings, price changes, and availability in specific locations
- **Data Journalism** — Collect real estate data for housing market reports and visualizations
- **Academic Research** — Gather property data for urban planning, economic, or housing studies

## 🔧 Tips for Best Results

1. **Start small** — Set `maxPages: 1` first to test your filters and preview results
2. **Use Auto-Complete first** — Always get Idealista location IDs from the [Auto-Complete actor](https://apify.com/burbn/idealista-auto-complete)
3. **Combine filters** — Use price, size, bedrooms, and amenity filters together to get exactly what you need
4. **Use pagination wisely** — Set `maxPages: 0` to scrape ALL pages (can be thousands of listings!)
5. **Export in your preferred format** — Download property data in JSON, CSV, or Excel

## 🔗 Related Actors

If you're looking for more Idealista data, check out our other scrapers:

- [**Idealista Auto-Complete**](https://apify.com/burbn/idealista-auto-complete) 📍 — Find Idealista location IDs for any city, neighborhood, or area.

## 🏷️ Tags

`idealista` `idealista scraper` `idealista properties` `idealista api` `idealista real estate` `idealista rent` `idealista sale` `property scraper` `real estate scraper` `real estate data` `property search` `rental properties` `properties for sale` `italy real estate` `spain real estate` `portugal real estate` `idealista crawler` `idealista extractor` `property prices` `property listings` `apartment search` `house search` `real estate api` `property data scraper` `idealista italy` `idealista spain` `idealista portugal`

## 🎁 Get $5 Free Apify Credits

New to Apify? [Sign up using this link](https://apify.com/?fpr=free-credits) and get **$5 free credits** to start scraping Idealista right away! No credit card required.

## 📞 Support

For questions, feedback, or issues with this Idealista property scraper, please contact us through Apify or open an issue.

---

**Happy scraping Idealista! 🏠✨**