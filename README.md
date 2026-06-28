[Idealista Scraper](https://apify.com/lukass/idealista-scraper?fpr=data)

# Actor - Idealista Scraper

## Idealista scraper

Since Idealista doesn't provide an API this actor should help you to retrieve data from it.

The Idealista data scraper supports the following features:

- Scrape property details - You can scrape attributes like property images, price, features and many more. You can find details below.
- Scrape for sale properties - If you are looking for a property which is for sale, you can directly target them.
- Scrape rental properties - Rental properties can be directly targeted.
- Scrape by keyword - You can use location-wise keywords to search specific search lists. Also you can directly point out rental, for sale or sold properties on this feature.
- Scrape properties by filter - Auto detection of URLs helps you to directly copy/paste the URLs into the scraper to apply any filtering you like.
- Through the new policy of web the exact location of some properties is hidden. So the scraper now get center of map which is accessible from detail of property.

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Realtor that should be visited. Required fields are:

| Field | Type | Description |
| --- | --- | --- |
| district | String | (optional) Keyword that can be searched in Realtor search engine. |
| country | String | (required) Select country where your search would be. |
| operation | String | (required) sale | rent |
| propertyType | String | (optional) You can choose property type (default **homes**) |
| maxItems | Integer | (optional) You can limit scraped products. This should be useful when you search through the big subcategories. |
| endPage | Integer | (optional) Final number of page that you want to scrape. Default is 50 pages. This option overrides maxItems. |
| startUrls | Array | (optional) List of Idealista URLs. You should only provide property detail or search URLs(beta) |
| proxy | Object | (required) Proxy configuration |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy). Scraper works only with **RESIDENTIAL** proxies right now.

## Example Result

```
{
	"url": "https://www.idealista.com/obra-nueva/109497241/",
	"title": "Flat in calle Cantalejo, 19",
	"id": "109497241",
	"price": 629328,
	"baths": 2,
	"rooms": 2,
	"address": "calle Cantalejo, 19",
	"hideAddress": true,
	"latitude": 40.4745112,
	"longitude": -3.7368474,
	"typology": "flat",
	"photos": [
		{
			"url": "https://img4.idealista.com/blur/480_360_mq/0/id.pro.es.image.master/a9/f6/68/1356345714.webp",
			"tag": "facade"
		},
		{
			"url": "https://img4.idealista.com/blur/480_360_mq/0/id.pro.es.image.master/4d/65/a6/1356345652.webp",
			"tag": "swimmingPool"
		},
		.
		.
		.
	],
	"listingUpdate": null,
	"contacts": {
		"commercialName": "Grupo Ibosa",
		"contactName": "NR Village homes",
		"phone1": {
			"phoneNumber": "919388896",
			"formattedPhone": "919 38 88 96",
			"prefix": "34",
			"phoneNumberForMobileDialing": "+34919388896",
			"nationalNumber": true
		}
	}
}
```

##### Tip

When you want to have a filtering over a search URL; go to Idealista, create filters over the serach list and copy and paste the link as one of the **startUrl**.

## Bugs, fixes, updates and changelog

If you have any feature requests you can create an issue from [here](https://github.com/laster04/Idealista-scraper/issues).
[Here](https://github.com/laster04/Idealista-scraper/blob/main/CHANGELOG.md) is changelog with new features and bugfixes info.