[Idealista Scraper](https://apify.com/igolaizola/idealista-scraper?fpr=data)

> 💼 If you're looking to scrape **agencies instead of properties**,
> 
> check this actor instead: 👉 [igolaizola/idealista-agency-scraper](https://apify.com/igolaizola/idealista-agency-scraper?fpr=ig)

## 🤖 What does Idealista-Scraper do?

Idealista-Scraper enables you to easily get data from [idealista.com](https://idealista.com) for a very low price.

It can scrape:

- 🏘️ Properties for **sale** in Spain, Italy, and Portugal
- 🔑 Properties for **rent** in Spain, Italy, and Portugal

## 💡 Why scrape idealista.com?

idealista.com has thousands of properties listed and is a great source of data for Real Estate professionals, investors, and anyone looking to buy or rent a property.
With Idealista-Scraper, you can get the data you need to make informed decisions about your next property purchase or rental.

Here are just some of the ways you could use that data:

- 📈 Analyze market trends and property price fluctuations in specific areas
- 👀 Monitor competitive pricing for real estate agencies and investors
- 🎯 Generate leads for real estate businesses
- 📊 Research rental yields and investment opportunities in different neighborhoods

## 🚀 How to scrape idealista.com

It's easy to scrape [idealista.com](https://idealista.com) with Idealista-Scraper. Just follow these few steps and you'll get your data in minutes:

1. Click **Try for free**
2. Enter the **operation**, **property type**, **country**, and **location**
3. (Optional) Set filters like price, size, bedrooms, etc.
4. Click **Run**
5. When the run finishes, preview or download your data from the **Dataset** tab
6. Click **All fields** to view all available data for each property and choose json or csv format.

## ⚠️ Important Warnings

- **Max items > 2500**: If `maxItems` is **greater than 2500**, the location will be **automatically split into sub-locations**. This **affects ordering** (results are grouped by sub-locations), so you might not get a strict global sort.
- **Fetch details** (`fetchDetails`): Adds **1 extra request per property** and is **~50× slower overall**. This feature is in **beta**; use with caution.
- **Fetch stats** (`fetchStats`): Adds **1 extra request per property** and is **~50× slower overall**. Produces a `_stats` field per property. This feature is in **beta**; use with caution.

## 💳 How much will it cost to scrape idealista.com?

Apify provides you with $5 free usage credits every month on the [Apify Free plan](https://apify.com/pricing). You can try and test Idealista-Scraper for free with the Free plan for a limited time.

However, if you need to get more data regularly from idealista.com, you should get an Apify subscription. We recommend our [$49/month Personal plan](https://apify.com/pricing) – this plan covers the costs of Idealista-Scraper and numerous executions.

## 📝 Input Parameters

You can provide either a **city name** or an **Idealista Location ID** for `location`. Find the Location ID with the **[Idealista Location Search Tool](https://igolaizola.github.io/idealista-scraper)**.

If you already know the listing codes, you can set `propertyCodes` to fetch those properties directly. When `propertyCodes` is provided, `location`, `fetchDetails`, and all filtering options are ignored. The actor always returns `_details` for each code (and `_stats` if `fetchStats` is enabled).

### Required

| Parameter | Options / Example | Description |
| --- | --- | --- |
| `operation` | `sale` | `rent` | Listing operation |
| `propertyType` | `homes`, `newDevelopments`, `offices`, `premises`, `garages`, `lands`, `storageRooms`, `buildings`, `bedrooms` | Type of property |
| `country` | `es` | `pt` | `it` | Country |
| `location` | `"Madrid"` or `"0-EU-ES-28-07-001-079"` | City name or Idealista Location ID |

### Core options

| Parameter | Type / Options | Description |
| --- | --- | --- |
| `propertyCodes` | Array of strings, e.g. `["12345678","87654321"]` | Fetch specific properties by code. Overrides location and filters; always populates `_details`. |
| `maxItems` | Integer (default **50**, `0` = unlimited) | **Recommended ≤ 2500**. If `> 2500`, the actor splits the location into sub-locations and ordering is grouped. |
| `sortBy` | `relevance`, `closest`, `lowestPrice`, `highestPrice`, `mostRecent`, `leastRecent`, `highestPriceReduction`, `lowestPriceM2`, `highestPriceM2`, `biggest`, `smallest`, `highestFloors`, `lowestFloors` | Sorting method for results |
| `fetchDetails` | Boolean (default `false`) | Fetch a detailed page per property → adds `_details` (beta). **Much slower & costlier**. |
| `fetchStats` | Boolean (default `false`) | Fetch per-listing statistics → adds `_stats` (beta). **1 extra request per property, ~50× slower overall**. |
| `minPrice` | **String** (default `"0"`) or preset steps: `"500"`–`"3000"` (rent) and `"50000"`–`"4000000"` (sale) | Minimum price (`"0"` = any) |
| `maxPrice` | **String** (default `"0"`) or preset steps: `"500"`–`"3000"` (rent) and up to `"4000000"` (sale) | Maximum price (`"0"` = any) |
| `minSize` | **String** (default `"0"`) or preset steps (m²): `"60"`, `"80"`, `"100"`, …, `"300"` | Minimum size in m² (`"0"` = any) |
| `maxSize` | **String** (default `"0"`) or preset steps (m²): `"60"`, `"80"`, `"100"`, …, `"300"` | Maximum size in m² (`"0"` = any) |
| `publicationDate` | `""` (any), `Y` (last 48h, only for `sale` operation), `T` (last 24h, only for `rent` operation), `W` (last week), `M` (last month) | Filter by publication date |

### Advanced filters

- `rentalTypes` (array, only for `rent`): `["longTerm","seasonal"]` (long-term residential, short-term)
- `bedrooms` (array): `["studio","1","2","3","4"]` (leave empty for any)
- `bathrooms` (array): `["1","2","3"]` (leave empty for any)
- `homeType` (array): `["flat","penthouse","duplex","detachedHouse","semiDetachedHouse","terracedHouse","countryHouse","apartment","villa","loft"]`
- `condition` (array): `["newDevelopment","good","renew"]`
- `propertyStatus` (array): `["bareOwnership","tenanted","illegallyOccupied","free"]`
- `floor` (array): `["topFloor","intermediateFloor","groundFloor"]`

### Amenities & features (booleans)

`airConditioning`, `fittedWardrobes`, `lift`, `balcony`, `terrace`, `exterior`, `garage`, `garden`, `swimmingPool`, `storageRoom`, `accessible`, `seaViews`, `luxury`, `plan` (floor plan), `virtualTour`.

### Agency filter

- `agency` (string): Filter properties by agency. Use the slug from the agency page URL, e.g., `engel-volkers` in `https://www.idealista.com/pro/engel-volkers/`.

### Proxy

Use Apify's proxy editor via `proxyConfiguration`:

- `useApifyProxy: true`
- (Recommended) `apifyProxyGroups: ["RESIDENTIAL"]`

> Residential proxies help prevent detection and IP blocking.

### Example input

```
{
  "maxItems": 100,
  "operation": "sale",
  "propertyType": "homes",
  "country": "es",
  "location": "0-EU-ES-28-07-001-079",
  "sortBy": "mostRecent",
  "fetchDetails": false,
  "fetchStats": false,
  "minPrice": 200000,
  "maxPrice": 500000,
  "minSize": 80,
  "maxSize": 120,
  "publicationDate": "W",
  "bedrooms": ["2", "3"],
  "bathrooms": ["2"],
  "homeType": ["flat", "penthouse"],
  "condition": ["newDevelopment", "good"],
  "propertyStatus": [],
  "floor": ["intermediateFloor"],
  "airConditioning": true,
  "fittedWardrobes": true,
  "lift": true,
  "balcony": false,
  "terrace": false,
  "exterior": true,
  "garage": true,
  "garden": false,
  "swimmingPool": false,
  "storageRoom": true,
  "accessible": false,
  "seaViews": false,
  "luxury": false,
  "plan": false,
  "virtualTour": false,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"]
  }
}
```

## 📊 Results

You'll get a list of property objects similar to Idealista's listing data.
If `fetchDetails: true`, each item includes an extra field: **`_details`** with detailed page data (beta).
If `fetchStats: true`, each item includes an extra field: **`_stats`** with per-listing statistics (beta).

```
[
  {
    "propertyCode": "106316721",
    "thumbnail": "https://img4.idealista.com/blur/WEB_LISTING-M/0/id.pro.es.image.master/46/12/06/1279185415.webp",
    "externalReference": "21",
    "numPhotos": 23,
    "floor": "3",
    "price": 105000,
    "priceInfo": {
      "price": {
        "amount": 105000
      }
    },
    "propertyType": "flat",
    "operation": "sale",
    "size": 78,
    "exterior": true,
    "rooms": 3,
    "bathrooms": 1,
    "address": "plaza Labradores, 9 --11",
    "province": "La Rioja",
    "municipality": "Ezcaray",
    "district": "",
    "country": "es",
    "locationId": "0-EU-ES-26-02-002-061",
    "latitude": 42.3203813,
    "longitude": -3.0147614,
    "showAddress": true,
    "url": "https://www.idealista.com/inmueble/106316721/",
    "description": "Ezcaray ofrece algunas de las mejores vistas a las montañas en La Rioja, convirtiéndolo en un destino ideal para los amantes de la naturaleza y la aventura.     Desde esta vivienda lo puedes comprobar! Gracias a su altura y orientación vas a poder disfrutar de las mejores vistas de Ezcaray.     Tiene tres habitaciones bien orientadas, una de ellas con mirador y balcón orientados al sur, salón, cocina amplia y baño completo.     Calefacción con calefactor de leña e instalación de radiadores.     Merece la pena llamar y concertar una visita!",
    "hasVideo": true,
    "status": "renew",
    "newDevelopment": false,
    "favourite": false,
    "newProperty": false,
    "multimedia": {
      "images": [
        {
          "url": "https://img4.idealista.com/blur/WEB_LISTING-M/0/id.pro.es.image.master/46/12/06/1279185415.webp",
          "tag": "views"
        },
        {
          "url": "https://img4.idealista.com/blur/WEB_LISTING-M/0/id.pro.es.image.master/56/0f/43/1279185423.webp",
          "tag": "kitchen"
        },
        {
          "url": "https://img4.idealista.com/blur/WEB_LISTING-M/0/id.pro.es.image.master/1c/91/45/1279185430.webp",
          "tag": "livingRoom"
        },
        {
          "url": "https://img4.idealista.com/blur/WEB_LISTING-M/0/id.pro.es.image.master/4d/03/c6/1279185433.webp",
          "tag": "bedroom"
        }
      ],
      "virtual3DTours": []
    },
    "contactInfo": {
      "commercialName": "INMOBILIARIA  LA ZALAYA ",
      "contactName": "INMOBILIARIA  LA ZALAYA ",
      "userType": "professional",
      "contactMethod": "all",
      "phone1": {
        "phoneNumber": "941776986",
        "formattedPhone": "941 77 69 86",
        "prefix": "34",
        "phoneNumberForMobileDialing": "+34941776986",
        "nationalNumber": true
      },
      "agencyLogo": "https://st3.idealista.com/9e/99/38/inmobiliaria-la-zalaya.gif",
      "micrositeShortName": "inmobiliaria-la-zalaya",
      "totalAds": 0
    },
    "hasLift": false,
    "parkingSpace": {
      "hasParkingSpace": false,
      "isParkingSpaceIncludedInPrice": false
    },
    "priceByArea": 1346,
    "features": {
      "hasSwimmingPool": false,
      "hasTerrace": false,
      "hasAirConditioning": false,
      "hasBoxRoom": false,
      "hasGarden": false
    },
    "detailedType": {
      "typology": "flat"
    },
    "suggestedTexts": {
      "subtitle": "",
      "title": "Piso en plaza Labradores, 9 --11"
    },
    "hasPlan": false,
    "has3DTour": false,
    "has360": false,
    "hasStaging": false,
    "isOnlineBookingActive": false,
    "ribbons": [],
    "topNewDevelopment": false,
    "topPlus": false,
    "preferenceHighlight": false,
    "urgentVisualHighlight": false,
    "visualHighlight": false,
    "topHighlight": false,
    "_details": {
      /* present only when fetchDetails=true (beta) */
    },

    "_stats": {
      /* present only when fetchStats=true (beta) */
      "views": { "value": 6539, "text": "6,539 views" },
      "contactMails": { "value": 18, "text": "18 email contacts" },
      "sentToFriend": { "value": 1, "text": "1 time sent to friends" },
      "favorites": { "value": 266, "text": "saved as favourite 266 times" }
    }
  }
  ...
]
```

## 🌍 Proxy

Idealista-Scraper uses Apify Residential Proxies to prevent detection and IP blocking.
Apify Proxy is a rotating proxy service that provides a pool of IP addresses.
This way, Idealista-Scraper can make a large number of requests to idealista.com without being blocked.

## ⚖️ Is it legal to scrape idealista.com?

Note that personal data is protected by GDPR in the European Union and by other regulations around the world. You should not scrape personal data unless you have a legitimate reason to do so. If you're unsure whether your reason is legitimate, consult your lawyers. We also recommend that you read our blog post: [is web scraping legal?](https://blog.apify.com/is-web-scraping-legal/)