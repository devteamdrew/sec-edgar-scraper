# SEC EDGAR Scraper – 10-K, 8-K & Form D Funding Filings

SEC EDGAR scraper for 10-K, 10-Q, 8-K, S-1, 13F and Form D filings. Full-text search, every filing for a list of tickers/CIKs, or a Form D startup funding feed (amount raised, industry, state, executives) from the official SEC APIs. No API key. CSV/JSON.

**[Run it on Apify →](https://apify.com/devteamdrew/sec-edgar-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=hero)** (pay per result, free Apify account to start)


**SEC EDGAR Scraper** by Moxie: fast, reliable and polite, built on official/public data sources.

## What can it do?

- Startup funding leads: new Form D filings by industry and state, with amount raised and executives
- Monitoring new 8-K events for a watchlist (incremental mode)
- Finding companies that mention a topic (e.g. AI, tariffs) in 10-Ks
- Building financial NLP and RAG datasets
- Due diligence and competitive research

## Data source

Official SEC EDGAR APIs (`efts.sec.gov` full-text search and `data.sec.gov` submissions) and the Form D XML in each filing's EDGAR archive folder, used within the SEC fair-access policy (declared User-Agent, under 10 requests/second).

## Features

- **Pay only for results** (pay-per-event pricing, no monthly rental)
- **Incremental mode**: scheduled runs return only items you haven't received before
- **LLM-ready output**: optional compact Markdown per item for RAG / AI agents
- **Polite rate limiting** with automatic retries and backoff
- Clean, flat JSON you can export as CSV, Excel, JSON or via API


## Quick start

1. Create a free account at [apify.com](https://apify.com/devteamdrew/sec-edgar-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=quickstart) and copy your API token.
2. `export APIFY_TOKEN=...`
3. Run one of the examples:

```bash
bash examples/run.sh          # curl
node examples/run.js          # JavaScript (apify-client)
python examples/run.py        # Python (apify-client)
```

Example input ([examples/input.json](examples/input.json)):

```json
{
  "mode": "fullTextSearch",
  "query": "\"web scraping\"",
  "forms": [
    "10-K"
  ],
  "startDate": "2025-01-01",
  "maxItems": 20
}
```

## FAQ

**Does it download the full documents?**
It returns direct links to the filing index and primary document; feed those to a crawler or LLM as needed.

**How far back does full-text search go?**
EDGAR full-text search covers filings from 2001 onwards.

**What is a Form D?**
A notice companies file with the SEC within 15 days of first selling securities in a private (Regulation D) offering, such as a seed or Series A round. It shows the amount raised so far, the offering size, industry, state, year of incorporation and the executives and directors.

**How do I get this week's tech funding rounds?**
Set the mode to Form D funding filings and industries to `Technology`, e.g. input `{"mode": "formD", "industries": ["Technology"], "minAmountSold": 1000000}`. Results include the amount raised, offering size, state, year of incorporation and the executives named on the filing.

**How fresh is the Form D feed?**
Filings appear in EDGAR the day they are filed. Schedule a daily run with incremental mode to get only new funding rounds.

## Use with AI agents (MCP)

Add `https://mcp.apify.com/?actors=devteamdrew/sec-edgar-scraper` as an MCP server in Claude, Cursor or any MCP client.

## Pricing

See the [Apify Store page](https://apify.com/devteamdrew/sec-edgar-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=pricing) for current pay-per-result pricing.

## Sample data

Browse real sample rows, download a free CSV sample and see ready-made feeds at [rowsift.co.uk](https://rowsift.co.uk/feeds/sec-edgar-scraper/?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=sample-data).

## More data actors

- [Bluesky Scraper – Posts, Profiles & Search](https://apify.com/devteamdrew/bluesky-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [UK Companies House Scraper – Companies & Directors](https://apify.com/devteamdrew/companies-house-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [UK Planning Applications Scraper – 400+ Councils & Postcodes](https://apify.com/devteamdrew/uk-planning-applications?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [Hacker News Scraper – Stories, Comments & Jobs](https://apify.com/devteamdrew/hacker-news-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [npm Package Scraper – Downloads & Dependencies](https://apify.com/devteamdrew/npm-package-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [GitHub Trending Scraper – Repos, Stars & Developers](https://apify.com/devteamdrew/github-trending-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [Mastodon Scraper – Fediverse Hashtags, Accounts & Trends](https://apify.com/devteamdrew/mastodon-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [Lemmy Scraper – Posts, Comments & Communities (Fediverse)](https://apify.com/devteamdrew/lemmy-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [arXiv Scraper – Paper Search, Abstracts & Authors](https://apify.com/devteamdrew/arxiv-scraper?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [UK Government Tenders Scraper – Contracts Finder, Find a Tender](https://apify.com/devteamdrew/uk-public-tenders?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [UK CQC Care Homes & Providers Scraper – Ratings & Care Leads](https://apify.com/devteamdrew/uk-cqc-care-providers?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [SAM.gov Scraper – Federal Contract Opportunities, No API Key](https://apify.com/devteamdrew/sam-gov-opportunities?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [UK Operator Licence Scraper – HGV & Bus Operators (DVSA VOL)](https://apify.com/devteamdrew/uk-operator-licences?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [USAspending Federal Awards Scraper – Contracts & Grants](https://apify.com/devteamdrew/usaspending-awards?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)
- [EU Tenders Scraper – TED Public Procurement Notices](https://apify.com/devteamdrew/eu-ted-tenders?utm_source=github&utm_medium=readme&utm_campaign=sec-edgar-scraper&utm_content=more)

## License

Examples in this repository are MIT licensed. The actor itself runs on the Apify platform.
