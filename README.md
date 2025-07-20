# CineSeek Movie Discovery App

CineSeek is a modern movie discovery application built with Next.js, TypeScript, and Tailwind CSS. It integrates the MoviesDatabase API to enable users to explore millions of movies, series, episodes, and actor data. This README provides an overview of the MoviesDatabase API integration.

---

## 📌 API Overview

The MoviesDatabase API offers comprehensive and updated data for:

- Over **9 million titles** (movies, series, episodes)
- Over **11 million actors**, cast, and crew members
- Data includes trailers, awards, full biographies, images, ratings, episode listings, and more
- Recent titles are updated weekly; ratings are updated daily
- All endpoints return an object with a `results` key. Paged endpoints also return `page`, `next`, and `entries`.

---

## 📦 Version

Latest documented version on [RapidAPI](https://rapidapi.com/SAdrian/api/moviesdatabase): _Unspecified (assume latest production release)_

---

## 🚀 Available Endpoints

### 🎬 Titles
- **`/titles`** – Get multiple titles based on filters
- **`/titles/{id}`** – Get a single title by IMDb ID
- **`/x/titles-by-ids`** – Get titles by a list of IMDb IDs
- **`/titles/{id}/ratings`** – Get rating and vote count for a title
- **`/titles/x/upcoming`** – List upcoming titles

### 📺 Series & Episodes
- **`/titles/series/{id}`** – Get episodes for a series
- **`/titles/seasons/{id}`** – Get number of seasons
- **`/titles/series/{id}/{season}`** – Get episodes in a specific season
- **`/titles/episode/{id}`** – Get detailed info on a single episode

### 🔍 Search
- **`/titles/search/keyword/{keyword}`** – Search titles by keyword
- **`/titles/search/title/{title}`** – Search titles by full or partial name
- **`/titles/search/akas/{aka}`** – Search titles by alternative names

### 🎭 Actors
- **`/actors`** – Get a list of actors
- **`/actors/{id}`** – Get details about a specific actor

### ⚙️ Utilities
- **`/title/utils/titleType`** – Get available title types
- **`/title/utils/genres`** – Get available genres
- **`/title/utils/lists`** – Get predefined movie lists (e.g. top-rated, most popular)

---

## 📡 Request and Response Format

- **All query parameters are optional** unless otherwise specified
- Endpoints typically return:

```json
{
  "results": [...],
  "page": 1,
  "next": 2,
  "entries": 10
}

```
## Authentication
To access the MoviesDatabase API, you must authenticate your requests using an API key.

### Authentication Method:

Include your RapidAPI key in the headers of every request:

http
Copy
Edit
x-rapidapi-key: YOUR_API_KEY
x-rapidapi-host: moviesdatabase.p.rapidapi.com
Content-Type: application/json
Obtain your API key by subscribing to the API on RapidAPI.

Store your API key securely (e.g., in .env.local) and never expose it publicly.

## Error Handling
The API uses standard HTTP status codes to communicate success or failure:

200 OK: Request successful.

400 Bad Request: The request is invalid (e.g., missing or wrong parameters).

401 Unauthorized: Missing or invalid API key.

404 Not Found: Requested resource does not exist.

429 Too Many Requests: Rate limit exceeded.

500 Internal Server Error: Server encountered an error.

Best Practice: Always check for response.ok in your fetch or API call, and use try/catch to gracefully handle errors and show user-friendly messages.

## Usage Limits and Best Practices
The API enforces rate limiting based on your RapidAPI subscription plan.

Use pagination (limit and page query parameters) to reduce payload size.

Cache frequent or static data like genres or lists to minimize API calls.

Use the info query parameter to request only needed fields to improve performance.

Protect your API keys by using environment variables and server-side API routes.

Implement retry logic and error boundaries to improve resilience.