[Dead Link Crawler](https://apify.com/practicaltools/dead-link-crawler?fpr=data)

# 🕷️ Dead-Link Watchdog

### Automatic, affordable link-health monitoring for any website

---

## 🚀 Overview

**Dead-Link Watchdog** keeps your website clean and reliable by automatically scanning for broken, redirected, or slow links — not just 404s.

It’s fast, cloud-based, and costs **only $0.0008 per link checked**.

That means you can audit **1 000 links for $0.80** or a full 10 000-page site for under $8.

Built on [Crawlee](https://crawlee.dev) and powered by Apify’s built-in scheduler, it runs in the background so you never need to worry about stale URLs or failing redirects again.

---

## 💡 Key features

- **🔍 Comprehensive checks** — flag any HTTP status codes you choose:

default = `400+`, or pick specific ones like

`400 401 403 404 410 429 500 502 503 504 301 302`.
- **💸 Ultra-low price** — just **$0.0008 per link checked** (1 000 links = $0.80).
- **📅 Fully schedulable** — use Apify’s built-in scheduler to run daily, weekly, or monthly scans automatically.
- **📊 Structured output** — all results saved to your Apify Dataset (viewable online or exportable as CSV / JSON).
- **⚡ Zero setup** — no proxies, servers, or local installs required.
- **🧩 Configurable depth & limits** — control both crawl depth (`maxCrawlDepth`) and total pages (`maxRequestsPerCrawl`).

---

## 🧰 Typical use cases

| 🧩 Scenario | Description |
| --- | --- |
| 🧱 **Website QA** | Catch broken or redirected links before users do. |
| 🔍 **SEO health checks** | Detect redirect chains, 404s, and server errors that hurt rankings. |
| 📚 **Docs maintenance** | Keep documentation and changelogs clean across hundreds of internal/external links. |
| 📢 **Agency reports** | Schedule weekly link-health reports for multiple client domains. |

---

## ⚙️ How it works

1. Start from your domain or sitemap.
2. The actor crawls pages up to your chosen depth (`maxCrawlDepth`).
3. Each `<a href>` link is tested via a lightweight HEAD request.
4. Any link returning a *flagged* status code is recorded with:

- Source page
- Target URL
- HTTP status code
- Response latency (ms)
- Timestamp

All results appear instantly in your **Apify Dataset** — ready to export or integrate into dashboards.

---

## 🧾 Input parameters

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| **`startUrls`** | array | `[{ "url": "http://www.example.com" }]` | One or more URLs or sitemaps to start crawling from. |
| **`maxCrawlDepth`** | integer | `2` | How many link-levels deep to crawl from each start URL. |
| **`flagStatusCodes`** | array | `[]` | List of HTTP status codes to flag (e.g. `[404, 500]`). If left empty, all `400+` codes are flagged. |
| **`includeExternal`** | boolean | `false` | Whether to check links to external domains. |
| **`timeoutMs`** | integer | `8000` | Timeout in ms for each request. |
| **`maxRequestsPerCrawl`** | integer | `300` | Maximum number of pages to crawl (0 = unlimited). |

---

## 🧩 Example usage

### 🔹 One-off scan

Run manually on any domain to generate an instant link-health report.

### 🔹 Automated monitoring

1. Open your actor’s **Run** page.
2. Click **Schedule → New schedule**.
3. Choose frequency (daily, weekly, etc.) and your input parameters.
4. Save — your site will now be scanned automatically at that interval.

---

## 💸 Pricing

- **$0.0008 per link checked**

- 100 links → $0.08
- 1 000 links → $0.80
- 10 000 links → $8.00
- You control cost through `maxRequestsPerCrawl`.
- No hidden fees, no proxy charges.

---

## 📊 Output example

```
{
  "source": "https://example.com/about",
  "target": "https://example.com/missing-page",
  "status": 404,
  "latency": 120,
  "timestamp": "2025-10-25T13:10:00Z"
}
```