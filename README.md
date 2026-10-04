# InsightSocial OpenAPI spec

The OpenAPI 3.1 spec for the [InsightSocial API](https://www.insightsocial.app/docs):
239 GET endpoints for public data from Instagram, TikTok, Facebook, LinkedIn, X/Twitter,
Threads, YouTube, Reddit and Pinterest, behind one `x-api-key` header and one credit balance.

- **File:** [`openapi.json`](openapi.json)
- **Live copy:** `https://api.insightsocial.app/v1/openapi.json` (free, no key)
- **Kept in sync:** a GitHub Action fetches the live spec every day and commits it when it
  changes, so this repo's history doubles as a changelog of the API surface.
- **Schema 2:** the spec describes schema 2 (`info.version` `2.0.0`), the response shape every
  key gets since 2026-10-04: one typed shape per entity (post, profile, comment, transcript)
  on every platform. See [Schema 2](https://www.insightsocial.app/docs/schema-2).
- **Legacy spec:** the previous document (`1.0.0`) is at
  `https://api.insightsocial.app/v1/openapi-legacy.json` until 2026-11-03, when the
  `InsightSocial-Version: legacy` header stops working. Do not generate new clients from it.

## Use it

Generate a client, or hand it to an agent framework that builds tools from OpenAPI:

```bash
# Any generator works; for example
npx @openapitools/openapi-generator-cli generate \
  -i https://api.insightsocial.app/v1/openapi.json -g python -o insightsocial-client
```

Import it into Postman, Insomnia or Bruno with the same URL.

Every call needs your key in the `x-api-key` header (`Authorization: Bearer` is not read).
Create one in the [portal](https://www.insightsocial.app/portal/api).

## What the spec tells you

- **Price per endpoint**, in credits, in each operation's description and in its `x-credits`
  field. Metered endpoints show
  a range: the top is held when the call starts, and you are charged what the call used.
- **Every parameter**, with type, allowed values and an example.
- **Free calls:** failed calls, empty results, `dry_run=1` and `Idempotency-Key` replays cost
  nothing. `/v1/credits`, `/v1/endpoints` and `/v1/openapi.json` are free.

For the same data as plain JSON with prices as fields, read the catalogue:
`GET https://api.insightsocial.app/v1/endpoints`.

## Related

- [insightsocial/cli](https://github.com/insightsocial/cli): CLI and MCP server (`npx -y insightsocial init`)
- [insightsocial/skills](https://github.com/insightsocial/skills): agent skills for Claude Code, Codex, Cursor and Gemini CLI
- [Docs](https://www.insightsocial.app/docs) · [Quickstart](https://www.insightsocial.app/docs/quickstart) · [API Explorer](https://www.insightsocial.app/portal/api/explorer)

Questions: [support@insightsocial.app](mailto:support@insightsocial.app)
