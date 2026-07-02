# CrawlGraph Datasets

Open datasets derived from [Common Crawl](https://commoncrawl.org/)'s public hyperlink graph, published by [CrawlGraph](https://crawlgraph.com/?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets).

Each dataset is a backlink-overlap study: for a category of tools, it maps which domains link to the whole set. The domains that link to most of a category are that niche's "universal linkers", the warmest outreach and link-building targets there are. Free to use with attribution.

## Datasets

| File | Category | Finding | Write-up |
|------|----------|---------|----------|
| [`data/seo-tools-universal-linkers.csv`](data/seo-tools-universal-linkers.csv) / [`.json`](data/seo-tools-universal-linkers.json) | 8 major SEO tools (ahrefs, semrush, moz, majestic, serpstat, se ranking, spyfu, surfer) | 9,687 linkers; 37 link to all 8; mostly trade media + roundups | [who links to every SEO tool](https://crawlgraph.com/blog/who-links-to-every-seo-tool?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) |
| [`data/crm-universal-linkers.csv`](data/crm-universal-linkers.csv) / [`.json`](data/crm-universal-linkers.json) | 8 major CRMs (hubspot, zoho, pipedrive, freshworks, close, copper, attio, salesflare) | 9,910 linkers; only 2 link to all 8 (Zapier, RingCentral); integration-driven | [only 2 domains link to every CRM](https://crawlgraph.com/blog/who-links-to-every-crm?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) |
| [`data/ai-agent-universal-linkers.csv`](data/ai-agent-universal-linkers.csv) / [`.json`](data/ai-agent-universal-linkers.json) | 8 AI agent frameworks (langchain, llamaindex, crewai, dify, flowise, langflow, autogpt, superagi) | 7,508 linkers; 5 link to all 8 (github, substack, analyticsvidhya + 2 product sites); dev platforms + young agent directories | [only 5 domains link to every AI agent framework](https://crawlgraph.com/blog/who-links-to-every-ai-agent-framework?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) |

## Schema

**CSV** columns:

| column | meaning |
|--------|---------|
| `domain` | a domain that links to several of the category's tools |
| `links_to_n_of_8` | how many of the 8 tools it links to (higher = more universal) |
| `cg_authority` | CrawlGraph authority score (0-100) for the linking domain |

Each CSV lists every domain linking to 6 or more of the 8 tools, sorted by overlap then authority. The JSON adds the per-tool subject stats (referring-domain counts and authority) plus the headline numbers.

## How it is built

CrawlGraph queries Common Crawl's open hyperlink graph (roughly 120M domains, 4.4B links, refreshed quarterly) directly with DuckDB, then intersects the referring domains of each tool in a category. No proprietary index, just open data. Platform and CDN noise (amazonaws, cloudfront, etc.) is filtered out.

## Run this for your own niche

Pick your two or three closest competitors and get the domains that link to several of them but not to you, ranked by authority. That is your niche's version of these lists. It is free, no signup, on the same data:

- **[crawlgraph.com/gap-analysis](https://crawlgraph.com/gap-analysis?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets)**

## License and attribution

The underlying link data is from Common Crawl (open data). These derived datasets are free to reuse; please credit [CrawlGraph](https://crawlgraph.com/?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) and link back. New categories are added over time.

Built by Pete at CrawlGraph.
