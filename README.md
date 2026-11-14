# CrawlGraph Datasets

Open datasets derived from [Common Crawl](https://commoncrawl.org/)'s public hyperlink graph, published by [CrawlGraph](https://crawlgraph.com/?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets).

Each dataset is a referring-domain overlap study: for a selected category of tools, it maps domains observed linking to several subjects in the source data. High overlap can help you find publications, directories and adjacent products worth researching. It is a starting shortlist, not proof that a current page links to a competitor or that an outreach pitch will succeed. Free to use with attribution.

## Datasets

| File | Category | Finding | Write-up |
|------|----------|---------|----------|
| [`data/seo-tools-universal-linkers.csv`](data/seo-tools-universal-linkers.csv) / [`.json`](data/seo-tools-universal-linkers.json) | 8 major SEO tools (ahrefs, semrush, moz, majestic, serpstat, se ranking, spyfu, surfer) | 9,687 linkers; 37 link to all 8; mostly trade media + roundups | [who links to every SEO tool](https://crawlgraph.com/blog/who-links-to-every-seo-tool?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) |
| [`data/crm-universal-linkers.csv`](data/crm-universal-linkers.csv) / [`.json`](data/crm-universal-linkers.json) | 8 major CRMs (hubspot, zoho, pipedrive, freshworks, close, copper, attio, salesflare) | 9,910 linkers; only 2 link to all 8 (Zapier, RingCentral); integration-driven | [only 2 domains link to every CRM](https://crawlgraph.com/blog/who-links-to-every-crm?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) |
| [`data/ai-agent-universal-linkers.csv`](data/ai-agent-universal-linkers.csv) / [`.json`](data/ai-agent-universal-linkers.json) | 8 AI agent frameworks (langchain, llamaindex, crewai, dify, flowise, langflow, autogpt, superagi) | 7,508 linkers; 5 link to all 8 (github, substack, analyticsvidhya + 2 product sites); dev platforms + young agent directories | [only 5 domains link to every AI agent framework](https://crawlgraph.com/blog/who-links-to-every-ai-agent-framework?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) |
| [`data/fintech-universal-linkers.csv`](data/fintech-universal-linkers.csv) / [`.json`](data/fintech-universal-linkers.json) | 8 fintech apps (stripe, wise, revolut, plaid, brex, ramp, mercury, chime) | 12,106 linkers; 8 link to all 8, all finance press + VC/startup databases | [8 domains link to every fintech app](https://crawlgraph.com/blog/who-links-to-every-fintech-app?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) |

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

## Turn a dataset into a research shortlist

1. Download the CSV for the category closest to your product and open it in a spreadsheet.
2. Start with high `links_to_n_of_8` rows, then use `cg_authority` as a secondary sorting signal.
3. Visit the domain and find the relevant article, directory entry or integration page. The CSV does **not** contain source-page URLs, anchor text or follow/nofollow attributes.
4. Check whether the page is current, covers your audience and already mentions your product. Remove irrelevant platforms, paid-placement offers and pages with no useful contribution you can make.
5. Record the page URL, why your product belongs there and your next action. A short, checked list is more useful than sending the same pitch to every domain.

These are historical observations from Common Crawl, not live link verification. The CSV/JSON files do not currently record an exact release ID or extraction cap. Consult each linked write-up for the available methodology, and do not treat the included totals as a complete census of the web.

## Run this for your own niche

Already have competitors in mind? Compare your domain with up to four competitors to find referring domains observed linking to them but not to you, ranked by overlap and CG Authority.

- **[See your first five ranked gaps](https://crawlgraph.com/gap-analysis?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets)** — the current free report asks for an email, with no card or account creation. Full results and exports require paid access; check the page for current terms.
- **[Use the API or MCP](https://crawlgraph.com/docs/api?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets)** — for scripts and AI-assisted research.

Your current query can use a newer source snapshot than these published datasets, so the results need not match the historical files.

## License and attribution

The underlying link data is from Common Crawl (open data). These derived datasets are free to reuse; please credit [CrawlGraph](https://crawlgraph.com/?utm_source=github&utm_medium=dataset&utm_campaign=crawlgraph-datasets) and link back. New categories are added over time.

Built by Pete at CrawlGraph.
