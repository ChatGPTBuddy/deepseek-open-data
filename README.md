# DeepSeek API pricing, releases & status — open data

[![DeepSeek API status](https://deepseek.ai/api/deepseek-badge?service=api)](https://deepseek.ai/is-deepseek-down)
[![DeepSeek chat status](https://deepseek.ai/api/deepseek-badge?service=chat)](https://deepseek.ai/is-deepseek-down)

Machine-readable DeepSeek data, checked against DeepSeek's own pages and updated daily:

| File | What's in it |
|---|---|
| [`data/deepseek-pricing.json`](data/deepseek-pricing.json) | Current DeepSeek API prices per model — off-peak and peak (peak = 2×), cache hit / miss / output — plus every earlier rate with the date it changed |
| [`data/deepseek-releases.json`](data/deepseek-releases.json) | Every entry in DeepSeek's API change log since May 2024, with model names and source |
| [`data/llm-api-pricing.json`](data/llm-api-pricing.json) | Standard-tier API prices for OpenAI GPT, Anthropic Claude and Google Gemini models, each with its official source |

Human-readable versions: [DeepSeek pricing](https://deepseek.ai/pricing) · [all DeepSeek models](https://deepseek.ai/deepseek-models) · [is DeepSeek down?](https://deepseek.ai/is-deepseek-down) · [data docs](https://deepseek.ai/deepseek-data)

## Use it

Straight from the web (CORS enabled, cached 1 hour):

```js
const res = await fetch("https://deepseek.ai/data/deepseek-pricing.json");
const { models } = await res.json();
const flash = models.find((m) => m.apiName === "deepseek-flash");
console.log(flash.offPeak.output); // USD per 1M output tokens
```

Or pin a version from this repo: `https://raw.githubusercontent.com/ChatGPTBuddy/deepseek-open-data/main/data/deepseek-pricing.json`

## Status badge for your README

```md
[![DeepSeek API status](https://deepseek.ai/api/deepseek-badge?service=api)](https://deepseek.ai/is-deepseek-down)
```

`service` can be `api`, `chat`, `platform` or `all`. The check runs live from deepseek.ai's server and is cached for one minute; how it works is explained on the [status page](https://deepseek.ai/is-deepseek-down).

## How the data is kept accurate

Prices and releases come from [DeepSeek's pricing page](https://api-docs.deepseek.com/quick_start/pricing) and [API change log](https://api-docs.deepseek.com/updates/); competitor prices from each vendor's official pricing page. A daily job checks DeepSeek for changes, and a person reviews every update before it is published. This repo mirrors the files from deepseek.ai once a day.

Found a wrong number? Open an issue.

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — free to use, also commercially. Please credit **"Data by [deepseek.ai](https://deepseek.ai/deepseek-data)"**.

deepseek.ai is an independent guide and is not affiliated with DeepSeek (Hangzhou DeepSeek Artificial Intelligence Co., Ltd.). For anything binding, check DeepSeek's own pricing page.
