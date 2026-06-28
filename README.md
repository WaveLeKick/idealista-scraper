[Idealista Scraper](https://apify.com/khadinakbar/idealista-scraper?fpr=data)

# 🏠 Idealista Scraper — Spain, Italy & Portugal Real Estate

Extract property listings from **Idealista.com**, Europe's largest real estate platform. Scrape prices, specs, GPS coordinates, agent contacts, amenities, energy ratings, and 28+ structured fields per listing — across Spain, Italy, and Portugal.

## What does Idealista Scraper do?

Idealista Scraper is an Apify actor that collects structured property data from [idealista.com](https://www.idealista.com) (Spain), [idealista.it](https://www.idealista.it) (Italy), and [idealista.pt](https://www.idealista.pt) (Portugal). It handles DataDome bot protection automatically using residential proxies and optional CapSolver integration, supports search queries and direct URLs, paginates through all result pages, and returns clean, analysis-ready JSON.

## Why use Idealista Scraper?

- **Pay only for what you scrape** — PAY_PER_EVENT pricing at $0.003/property (no flat monthly fee)
- **Supports all 3 Idealista domains** — Spain, Italy, Portugal in one actor
- **Two input modes** — search by location name OR paste any direct Idealista search URL
- **Full pagination** — automatically navigates all result pages up to your limit
- **MCP-ready** — semantic field names, fully compatible with Claude, ChatGPT, and Cursor via Apify's MCP server
- **28+ structured fields** per property including GPS coordinates, amenity flags, and energy ratings
- **DataDome bypass** — residential proxy + CapSolver integration for reliable access

## ⚠️ DataDome Bot Protection — Important Note

Idealista uses **DataDome** bot protection. To scrape reliably:

1. **Residential proxies are required** (included in default proxy configuration — do not switch to datacenter proxies)
2. **A CapSolver API key is strongly recommended** for handling visual CAPTCHA challenges. Without it, some runs may be blocked. Get your key at [capsolver.com](https://capsolver.com) — DatadomeSliderTask costs ~$0.004 per solve.

Add your CapSolver key to the `capsolverApiKey` field in the actor input. The actor will automatically detect and solve challenges during the run.

## What data does Idealista Scraper extract?

| Field | Type | Description |
| --- | --- | --- |
| `property_id` | string | Idealista unique ID |
| `url` | string | Direct link to property page |
| `title` | string | Listing title |
| `property_type` | string | homes / offices / premises / etc. |
| `operation` | string | sale or rent |
| `price` | number | Price in EUR |
| `price_per_sqm` | number | Computed €/m² for market comparison |
| `size_sqm` | number | Area in square meters |
| `rooms` | number | Number of bedrooms |
| `bathrooms` | number | Number of bathrooms |
| `floor` | string | Floor level |
| `address` | string | Street address |
| `neighborhood` | string | Neighborhood/district |
| `city` | string | City |
| `province` | string | Province/region |
| `country` | string | Country code (es/it/pt) |
| `latitude` | number | GPS latitude |
| `longitude` | number | GPS longitude |
| `description` | string | Full listing description |
| `thumbnail_url` | string | Primary photo URL |
| `images` | array | All photo URLs |
| `amenities` | object | terrace, lift, pool, AC, garage, garden, storage |
| `energy_rating` | string | EU energy certificate (A–G) |
| `agent_name` | string | Agency or seller name |
| `agent_type` | string | Professional or private |
| `agent_phone` | string | Contact phone number |
| `is_new_development` | boolean | New construction flag |
| `publication_date` | string | Listing publication date (ISO 8601) |
| `scraped_at` | string | Extraction timestamp |
| `source_url` | string | Source search page URL |

## How to use Idealista Scraper

### Option 1 — Search by location (recommended)

1. Set **Country** (Spain / Italy / Portugal)
2. Set **Operation** (For Sale or For Rent)
3. Set **Property Type** (Homes, Offices, Garages, etc.)
4. Set **Location** — use the location slug from the Idealista URL (e.g. `madrid`, `barcelona`, `roma`, `lisboa`)
5. Set **Max Results** — how many properties to return
6. (Optional) Add your **CapSolver API Key** for reliable DataDome bypass
7. Click Run

### Option 2 — Paste a direct search URL

1. Go to [idealista.com](https://www.idealista.com) and configure your search with filters (price range, bedrooms, amenities, etc.)
2. Copy the URL from your browser — e.g. `https://www.idealista.com/venta-viviendas/madrid/con-terraza/?ordenado-por=precio-asc`
3. Paste it into **Start URLs**
4. Set **Max Results** and click Run

### Code example — via Apify API

```
const { ApifyClient } = require('apify-client');
const client = new ApifyClient({ token: 'YOUR_TOKEN' });

const run = await client.actor('khadinakbaronline/idealista-scraper').call({
    operation: 'sale',
    propertyType: 'homes',
    location: 'madrid',
    country: 'es',
    maxResults: 100,
    capsolverApiKey: 'YOUR_CAPSOLVER_KEY',
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
console.log(items);
```

```
from apify_client import ApifyClient

client = ApifyClient('YOUR_TOKEN')
run = client.actor('khadinakbaronline/idealista-scraper').call(run_input={
    'operation': 'sale',
    'propertyType': 'homes',
    'location': 'barcelona',
    'country': 'es',
    'maxResults': 200,
    'capsolverApiKey': 'YOUR_CAPSOLVER_KEY',
})
items = list(client.dataset(run['defaultDatasetId']).iterate_items())
```

## 🤖 MCP Server Integration (AI Agents)

Idealista Scraper is fully compatible with the **[Apify MCP Server](https://apify.com/apify/actors-mcp-server)**, which lets AI agents like Claude, ChatGPT, and Cursor directly call Apify actors as tools.

### Connect via Apify MCP Server

Add the following to your MCP client configuration (e.g. Claude Desktop `claude_desktop_config.json`):

```
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "@apify/actors-mcp-server"],
      "env": {
        "APIFY_TOKEN": "YOUR_APIFY_TOKEN",
        "ACTORS": "khadinakbaronline/idealista-scraper"
      }
    }
  }
}
```

Once connected, your AI agent can call the scraper with natural language:

> "Scrape 50 homes for sale in Madrid from Idealista and return properties under €400,000"

### MCP Tool Schema

The actor exposes these input parameters as MCP tool arguments:

| Parameter | Type | Description |
| --- | --- | --- |
| `location` | string | City slug (e.g. `madrid`, `roma`, `lisboa`) |
| `country` | string | `es`, `it`, or `pt` |
| `operation` | string | `sale` or `rent` |
| `propertyType` | string | `homes`, `offices`, `garages`, etc. |
| `maxResults` | number | Max properties to return (1–10,000) |
| `startUrls` | array | Direct Idealista search URLs (optional) |
| `capsolverApiKey` | string | CapSolver key for CAPTCHA bypass (recommended) |

### Apify MCP Server — Actors Directory

Find this actor and thousands more at the **[Apify MCP Server Actors Directory](https://apify.com/store)**. The MCP server supports dynamic actor discovery — you can list available actors, check their schemas, and call them without writing any code.

Install the MCP server:

```
$npx @apify/actors-mcp-server
```

## Key-Value Store Output

In addition to the main dataset, each run writes a `SCRAPE_STATS` summary to the default Key-Value Store:

```
{
  "totalScraped": 50,
  "targetLocation": "madrid",
  "country": "es",
  "operation": "sale",
  "propertyType": "homes",
  "capsolverUsed": true,
  "captchasSolved": 2,
  "pagesScraped": 3,
  "durationSeconds": 145,
  "startedAt": "2025-01-15T10:00:00.000Z",
  "finishedAt": "2025-01-15T10:02:25.000Z"
}
```

## Pricing

This actor uses **PAY_PER_EVENT** billing — you only pay for actual properties scraped.

| Apify Plan | Price per property |
| --- | --- |
| FREE | $0.003 |
| BRONZE | $0.003 |
| SILVER | $0.0025 |
| GOLD | $0.002 |
| PLATINUM | $0.0015 |
| DIAMOND | $0.001 |

**Example costs:**

- 100 properties ≈ $0.30
- 1,000 properties ≈ $3.00
- 10,000 properties ≈ $30.00

Much cheaper than flat monthly subscriptions ($15–$19/month) if you scrape fewer than 5,000 properties/month.

## Use cases

- **Real estate investors** — identify undervalued properties by price-per-m² across neighborhoods
- **Market analysts** — track price trends over time across cities or provinces
- **Real estate agencies** — competitive monitoring and lead generation
- **Property developers** — build valuation tools, market dashboards, or investment scoring models
- **AI pipelines** — feed structured property data into LLMs (via MCP) for analysis, Q&A, and recommendations
- **Academic researchers** — housing market studies across Spain, Italy, and Portugal

## Technical notes

- Uses **Playwright** browser automation with headful mode (`headless: false`) on Apify's xvfb display — this causes DataDome to serve a softer device-check interstitial rather than an immediate hard block
- Requires **Spanish Residential Proxies** to bypass DataDome (default proxy configuration is pre-set; do not change)
- **CapSolver** `DatadomeSliderTask` integration for automatic CAPTCHA solving (~$0.004/solve)
- Crawlee fingerprint injection (CDP-level) for Windows/macOS/Spanish locale
- Native `page.addInitScript()` patches for `navigator.webdriver`, `window.chrome`, permissions, and other automation signals
- Automatically handles cookie consent popups
- Full pagination — navigates all result pages
- Session pooling and retry logic for reliability
- Writes `SCRAPE_STATS` summary to Key-Value Store at end of each run

## Legal disclaimer

*This actor is intended for lawful data collection from publicly available sources. Users are responsible for compliance with applicable laws, Idealista's terms of service, and data protection regulations (GDPR, CCPA, etc.). Do not use this actor to collect personal data without a lawful basis, or to systematically copy Idealista's database.*