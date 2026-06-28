[Idealista Scraper](https://apify.com/axlymxp/idealista-scraper?fpr=data)

# Idealista Property Scraper

An [Apify](https://apify.com/) actor for scraping real estate listings from [Idealista.com](https://www.idealista.com/), Spain's leading real estate platform. This scraper extracts detailed property information including prices, features, locations, and more.

## 🚀 Features

- Scrapes property listings from Idealista.com
- Extracts comprehensive property details:

- Basic information (price, size, rooms, bathrooms)
- Location details (address, neighborhood, city, province)
- Property features and amenities
- Images and descriptions
- Energy certification
- Contact information
- Handles pagination automatically
- Respects website's robots.txt and implements polite scraping
- Stores results in structured format
- Supports various search filters

## 📋 Input Parameters

The actor accepts the following input parameters:

```
{
    "country": "es",
    "locationName": "Callosa de Segura, Alicante",
    "distance": 0,
    "locationId": "0-EU-ES-03-05-015-049",
    "propertyType": "homes",
    "sort": "desc",
    "operation": "sale",
    "order": "weigh",
    "locale": "en",
    "quality": "high",
    "gallery": true,
    "maxItems": 30,
    "numPage": 1
}
```

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `country` | String | Country code to search in (es: Spain, it: Italy, pt: Portugal) | `es` |
| `locationName` | String | Name of the location to search in | `Callosa de Segura, Alicante` |
| `locationId` | String | Idealista location ID | `0-EU-ES-03-05-015-049` |
| `propertyType` | String | Type of property to search for: - newDevelopments: New Developments - homes: Homes - offices: Offices - premises: Commercial Property - transfers: Transfers - garages: Garages - lands: Land - storageRooms: Storage Rooms - buildings: Buildings | `homes` |
| `sort` | String | Sort direction for results (asc/desc) | `desc` |
| `operation` | String | Type of operation (sale/rent) | `sale` |
| `order` | String | Field to order results by: - weigh: Relevance - price: Price - publicationDate: Publication Date - priceDown: Price Reduction - ratioeurm2: Price per m² - size: Size | `weigh` |
| `locale` | String | Language for results (en/es/it/pt) | `en` |
| `quality` | String | Quality of images (high/medium/low) | `high` |
| `gallery` | Boolean | Whether to include image gallery | `true` |
| `maxItems` | Integer | Maximum number of items per page (1-50) | `30` |
| `numPage` | Integer | Page number to start scraping from | `1` |

**Required Parameters:**

- `country`
- `propertyType`
- `operation`
- `locationName`
- `locationId`

**Note:** For locationName ane locationId , use actor [Idealista Location Scraper](https://apify.com/axlymxp/idealista-location-scraper)

**Note:** The actor uses Apify's proxy infrastructure by default to avoid IP-based blocking. You don't need to configure proxy settings manually.

## 📊 Output Dataset

The actor stores results in a dataset with the following schema:

```
{
    "propertyCode": "String - Unique property identifier",
    "url": "String - Property listing URL",
    "thumbnail": "String - Main property image URL",
    "numPhotos": "Number - Total number of photos",
    "price": "Number - Property price in euros",
    "priceInfo": {
        "price": {
            "amount": "Number - Price amount",
            "currencySuffix": "String - Currency symbol",
            "priceDropInfo": {
                "formerPrice": "Number - Previous price",
                "priceDropValue": "Number - Price reduction amount",
                "priceDropPercentage": "Number - Percentage of price reduction"
            }
        }
    },
    "propertyType": "String - Type of property (e.g., countryHouse)",
    "operation": "String - Sale or rent",
    "size": "Number - Size in square meters",
    "rooms": "Number - Number of rooms",
    "bathrooms": "Number - Number of bathrooms",
    "address": "String - Street address",
    "province": "String - Province name",
    "municipality": "String - Municipality name",
    "country": "String - Country code",
    "locationId": "String - Idealista location identifier",
    "latitude": "Number - Geographic latitude",
    "longitude": "Number - Geographic longitude",
    "description": "String - Full property description",
    "multimedia": {
        "images": [
            {
                "url": "String - Image URL",
                "tag": "String - Image type (e.g., bedroom, bathroom, livingRoom)"
            }
        ]
    },
    "contactInfo": {
        "phone1": {
            "phoneNumber": "String - Contact phone number",
            "formattedPhone": "String - Formatted phone number",
            "prefix": "String - Country prefix",
            "phoneNumberForMobileDialing": "String - Full international number",
            "nationalNumber": "Boolean - Is national number"
        },
        "contactName": "String - Contact person name",
        "userType": "String - Type of seller (private/professional)",
        "contactMethod": "String - Preferred contact method"
    },
    "features": {
        "hasSwimmingPool": "Boolean - Has swimming pool",
        "hasTerrace": "Boolean - Has terrace",
        "hasAirConditioning": "Boolean - Has air conditioning",
        "hasBoxRoom": "Boolean - Has storage room",
        "hasGarden": "Boolean - Has garden"
    },
    "parkingSpace": {
        "hasParkingSpace": "Boolean - Has parking",
        "isParkingSpaceIncludedInPrice": "Boolean - Parking included in price"
    },
    "priceByArea": "Number - Price per square meter",
    "detailedType": {
        "typology": "String - Main property type",
        "subTypology": "String - Specific property type"
    },
    "status": "String - Property condition",
    "hasVideo": "Boolean - Has video tour",
    "has3DTour": "Boolean - Has 3D tour",
    "has360": "Boolean - Has 360° view",
    "labels": [
        {
            "name": "String - Label identifier",
            "text": "String - Label display text"
        }
    ]
}
```

**Note:** Some fields may be null or missing depending on the property listing. The schema above represents all possible fields that can be returned by the scraper.

Key features of the output:

- Detailed price information including price history
- Comprehensive property features and amenities
- Complete multimedia content (images with tags)
- Precise location data including coordinates
- Contact information for the seller
- Property status and special features (video, 3D tour, etc.)

## Pagination and Search Results

- Apply your search parameters to search, and get the first page (numPage = 1)
- Check the total number of results from the key-value store
- Increment numPage to 2, and maintain the same search parameters
- Continue this process until you have retrieved all available results