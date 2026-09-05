# matt22.github.io
Compact index of Matthew Heard's public projects.

## Cosmic Lab API

A serverless REST API for practicing HTTP requests and working with real-world datasets. Built in Python and deployed on Cloudflare Workers, with Cloudflare Workers KV caching filtered query results.

[Try the airports API](https://api.cosmic-lab.workers.dev/api/v1/airports?state_code=CA&page=1) · [Source repository (private)](https://github.com/matt22/cosmic-lab-api)

### Technology and implementation

| Area | Technologies and features |
| --- | --- |
| Language | Python 3.13.2+, type annotations, standard-library query processing and JSON serialization |
| Serverless runtime | Cloudflare Python Workers, `WorkerEntrypoint`, Workers runtime SDK, asynchronous request handling |
| API | Versioned REST/HTTP GET endpoint, JSON responses, URL query parameters, state-code filtering, input validation, page-based pagination, structured errors with HTTP 400/404/405 status codes |
| Cache and storage | Cloudflare Workers KV, cache-aside reads and writes, versioned cache keys, cached result sets shared across pages, configurable three-hour TTL |
| Source data | Git-tracked flat JSON datasets; airport data bundled with the Worker |
| Data engineering | Python scripts for dataset extraction, transformation, validation, normalization and deduplication; CSV/TSV and compressed-data processing; Wikidata SPARQL and Open Library API ingestion |
| Development and deployment | Git/GitHub, `uv`, `pywrangler`, `workers-py`, dependency lockfiles, Wrangler JSONC configuration, Worker bindings and environment variables |
| Testing | Python `unittest`, asynchronous cache tests, fake KV storage, pagination and query-validation checks, bundled-data consistency checks |

**Available now:** `GET /api/v1/airports?state_code=CA&page=1`, with three airports per page and pagination metadata. Query results are cached in KV; the checked-in JSON remains the source of truth.

**Dataset collection:** 100 US airports, 1,000 movies, 1,000 cities, 1,000 books, and 100 fictional service incidents. Sources include FAA statistics, OurAirports, GeoNames, IMDb, Wikidata, and Open Library. Additional dataset endpoints and broader filtering/sorting are future work.
