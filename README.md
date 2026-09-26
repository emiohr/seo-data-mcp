# SEO Data MCP Server — keyword volume, backlinks, domain authority, Google Trends & tech stack for AI agents

Give Claude, Cursor, VS Code, Cline or any MCP client **live SEO data**: Google search volume and keyword difficulty (with AI Overview detection), backlinks and competitor link gap, domain authority, Google Trends, and the tech stack of any website. It's a remote MCP server with nothing to install: paste one URL, then ask your agent things like *"find easy-win keywords for cold brew coffee"* or *"which sites link to my competitors but not to me?"*.

The server is hosted by Apify ([`mcp.apify.com`](https://docs.apify.com/integrations/mcp)) and exposes five pay-per-use tools. You pay only for the data an agent actually fetches, with no subscription.

## Setup (1 minute)

Server URL:

```
https://mcp.apify.com?tools=jesting_grass/keyword-research-tool,jesting_grass/backlink-checker,jesting_grass/bulk-domain-authority-checker,jesting_grass/google-trends-api,jesting_grass/tech-stack-detector
```

**Claude Desktop / claude.ai**: Settings → Connectors → Add custom connector → paste the URL above, then sign in to Apify (a free account works).

**Claude Code**

```bash
claude mcp add --transport http seo-data "https://mcp.apify.com?tools=jesting_grass/keyword-research-tool,jesting_grass/backlink-checker,jesting_grass/bulk-domain-authority-checker,jesting_grass/google-trends-api,jesting_grass/tech-stack-detector"
```

**Cursor / VS Code / Cline / Windsurf** (`mcp.json`):

```json
{
  "mcpServers": {
    "seo-data": {
      "url": "https://mcp.apify.com?tools=jesting_grass/keyword-research-tool,jesting_grass/backlink-checker,jesting_grass/bulk-domain-authority-checker,jesting_grass/google-trends-api,jesting_grass/tech-stack-detector",
      "headers": { "Authorization": "Bearer YOUR_APIFY_TOKEN" }
    }
  }
}
```

Get a token at [console.apify.com](https://console.apify.com) → Settings → API & Integrations. Clients that support OAuth can drop the `headers` block and sign in instead.

## Tools

| Tool | What the agent gets | Price |
|---|---|---|
| [Keyword Research](https://apify.com/jesting_grass/keyword-research-tool) | Google search volume, keyword difficulty, intent, CPC, 12-month trend, SERP features incl. **AI Overview** flag, keyword ideas from a seed | $3 per 1,000 keywords, $1.50 per 1,000 ideas, plus $0.15 per Google Ads batch (per run, per 1,000 keywords) |
| [Backlink Checker](https://apify.com/jesting_grass/backlink-checker) | Every backlink (source page, anchor, dofollow, authority), referring domains, **competitor link gap** | $1 per 1,000 backlinks |
| [Bulk Domain Authority](https://apify.com/jesting_grass/bulk-domain-authority-checker) | Domain rank 0–100, referring domains, backlinks, dofollow ratio, 30-day changes | $8 per 1,000 domains |
| [Google Trends](https://apify.com/jesting_grass/google-trends-api) | Interest over time, rising and top related queries and topics, interest by region | $0.025 per comparison of up to 5 keywords; related queries, topics or regions $0.03 per keyword |
| [Tech Stack Detector](https://apify.com/jesting_grass/tech-stack-detector) | CMS, ecommerce platform, analytics, payments, CRM and hosting of any website | $0.02 per website |

Empty results are free for every tool.

## Example prompts

- "Find 10 low-difficulty keywords with 1,000+ monthly searches around *cold brew coffee*, and flag which ones show a Google AI Overview."
- "Compare the domain authority and referring domains of dev.to, hashnode.com and medium.com."
- "Which websites link to rothys.com and vivobarefoot.com but not to allbirds.com? Give me the 20 strongest."
- "Is interest in *standing desk* rising or falling in the US over the past 5 years? Show the rising related queries."
- "Which of these 30 stores run on Shopify, and which payment providers do they use?"

## Want just one tool?

Put only that tool in `?tools=`, for example `https://mcp.apify.com?tools=jesting_grass/backlink-checker`.

## Also available as

- Python / Node.js / cURL examples: [keyword-research-api](https://github.com/emiohr/keyword-research-api), [backlink-checker-api](https://github.com/emiohr/backlink-checker-api), [bulk-domain-authority-checker](https://github.com/emiohr/bulk-domain-authority-checker), [google-trends-api](https://github.com/emiohr/google-trends-api), [builtwith-wappalyzer-alternative](https://github.com/emiohr/builtwith-wappalyzer-alternative)

*Data comes from commercial SEO data providers. Not affiliated with Google, Ahrefs, Semrush or BuiltWith.*
