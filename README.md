[Dead Link Crawler](https://apify.com/actually_good_at_this/dead-link-crawler?fpr=data)

A dead link crawler built with Apify SDK that scans websites and identifies broken links (404, 500, etc.).

## Features

- Crawls all links on a website
- Detects broken links (4xx and 5xx status codes)
- Uses CheerioCrawler for fast static HTML crawling
- Respects robots.txt
- Customizable User-Agent
- Exports results to JSON/CSV/Excel

## Input

```
{
  "startUrl": "https://example.com",
  "maxPages": 100,
  "userAgent": "DeadLinkChecker/1.0"
}
```

## Output

Results are stored in the `broken-links` dataset with fields:

- `url`: The broken link URL
- `statusCode`: HTTP status code (404, 500, etc.)
- `checkedAt`: Timestamp
- `source`: Where the link was found

## Example

```
{
  "startUrl": "https://mywebsite.com",
  "maxPages": 50,
  "userAgent": "MySiteBot/1.0"
}
```

## How to Use

1. Deploy to Apify
2. Configure the input with your target URL
3. Run the crawler
4. Check the broken-links dataset for results