# Feed API V2 Overview
API V2 is the second version of our API, offering enhanced performance and new features.

- **Endpoints**: The base endpoint is `http://feed-api.stockic.in/ap1/v2`
- **Authentication**: All the requests need HTTP Header `X-API-Key: <api-key>` with the request. In case of using CURL: `curl -X <HTTP METHOD> -H 'X-API-Key: <API-KEY>' API_ENDPOINT` 

---

## Ping Endpoint
Ping test to check if the API Server is up.

**Request:**
```bash
GET /ping
```
**Response:**
```json
{
    "response": "pong!"
}
```
**Curl Command:** `curl -X GET -H <api-key> http://feed-api.stockic.in/api/v2/ping`

---

## Headlines Endpoint
Returns Top Headlines of the day from various countries. Currently, it's the news from all over the world.

**Request:**
```bash
GET /api/v2/headlines/<page-size>
```
**Response:**
```json
{
  "status": "ok",
  "totalResults": 29,
  "articles": [
    {
      "stockicID": "bdfcef5f9dcb62e574114ccd7e02c30974bdd768838eed919736ef6412c705b9",
      "source": "The Washington Post",
      "author": "Ben Noll",
      "title": "Where some of the coldest air of the season will hit in the U.S. this week - The Washington Post",
      "url": "https://www.washingtonpost.com/weather/2025/02/17/polar-vortex-subzero-cold-forecast-snow-ice-storm/",
      "urlToImage": "https://theintercept.com/wp-content/uploads/2017/01/the-washington-post-newspaper-2-1484771977.jpg",
      "publishedAt": "2025-02-17T11:55:23Z",
      "content": "A lobe of the polar vortex, a ring of freezing air typically found near the North Pole, will once again move into the central and eastern states this week, bringing some of the coldest air of the win… [+6433 chars]",
      "companyTags": [
        "Nvidia",
        "Google"
      ],
      "highlightsIndex": [
        [
          1,
          5
        ],
        [
          7,
          10
        ]
      ]
    }
  ]
}
```
**Curl Command:** `curl -X GET -H <api-key> http://feed-api.stockic.in/api/v2/headlines/<page-size>`

---

## Newsfeed Endpoint
Serves newsfeeds with page size and page numbers. Also contain the headlines in it. 

**Request:**
```bash
GET /newsfeed/<page-size>/<page-number>
```
**Response:**
```json
{
  "status": "ok",
  "totalResults": 29,
  "articles": [
    {
      "stockicID": "bdfcef5f9dcb62e574114ccd7e02c30974bdd768838eed919736ef6412c705b9",
      "source": "The Washington Post",
      "author": "Ben Noll",
      "title": "Where some of the coldest air of the season will hit in the U.S. this week - The Washington Post",
      "url": "https://www.washingtonpost.com/weather/2025/02/17/polar-vortex-subzero-cold-forecast-snow-ice-storm/",
      "urlToImage": "https://theintercept.com/wp-content/uploads/2017/01/the-washington-post-newspaper-2-1484771977.jpg",
      "publishedAt": "2025-02-17T11:55:23Z",
      "content": "A lobe of the polar vortex, a ring of freezing air typically found near the North Pole, will once again move into the central and eastern states this week, bringing some of the coldest air of the win… [+6433 chars]",
      "companyTags": [
        "Nvidia",
        "Google"
      ],
      "highlightsIndex": [
        [
          1,
          5
        ],
        [
          7,
          10
        ]
      ]
    }
  ]
}
```
**Curl Command:** `curl -X GET -H <api-key> http://feed-api.stockic.in/api/v2/newsfeed/<page-size>/<page-number>`

---

## Discover Endpoint
Categories of news can be accessed through this endpoint. 

Available categories: gainers, losers, software, finance, stocks, bonds, corporate, banking, technology, tax, geopolitics

**Request:**
```bash
GET /discover/<category>/<page-size>/<page-number> 
```
**Response:**
```json
{
  "status": "ok",
  "totalResults": 29,
  "articles": [
    {
      "stockicID": "8b372605672e3294e56bccb14f5d883cff191409ec4533f5e9ec64de220b3ed9",
      "source": "The Times of India",
      "author": "ETMarkets.com",
      "title": "Stock market update: Stocks that hit 52-week lows on NSE in today's trade",
      "url": "https://economictimes.indiatimes.com/markets/stocks/stock-watch/stock-market-update-stocks-that-hit-52-week-lows-on-nse-in-todays-trade/articleshow/118328196.cms",
      "urlToImage": "https://img.etimg.com/thumb/msid-82697732,width-1200,height-630,imgsize-184256,overlay-etmarkets/articleshow.jpg",
      "publishedAt": "2025-02-17T10:30:07Z",
      "content": "(What's moving Sensex and Nifty Track latest market news, stock tips, Budget 2025, Share Market on Budget 2025 and expert advice, on ETMarkets. Also, ETMarkets.com is now on Telegram. For fastest new… [+330 chars]",
      "companyTags": [
        "Nvidia",
        "Google"
      ],
      "highlightsIndex": [
        [
          1,
          5
        ],
        [
          7,
          10
        ]
      ]
    }
  ]
}
```
**Curl Command:** `curl -X GET -H <api-key> http://feed-api.stockic.in/api/v2/discover/<category>/<page-size>/<page-number>`

---

## Detail Endpoint
Fetching details about the news with news ID. Stockic has all it's tagged with news ID called stockicID to uniquely identify news. With just the stockicID, you can fetch all the information about it. 

**Request:**
```bash
GET /detail/<news-id>
```
**Response:**
```json
{
  "stockicID": "bdfcef5f9dcb62e574114ccd7e02c30974bdd768838eed919736ef6412c705b9",
  "source": "The Washington Post",
  "author": "Ben Noll",
  "title": "Where some of the coldest air of the season will hit in the U.S. this week - The Washington Post",
  "url": "https://www.washingtonpost.com/weather/2025/02/17/polar-vortex-subzero-cold-forecast-snow-ice-storm/",
  "urlToImage": "https://theintercept.com/wp-content/uploads/2017/01/the-washington-post-newspaper-2-1484771977.jpg",
  "publishedAt": "2025-02-17T11:55:23Z",
  "content": "A lobe of the polar vortex, a ring of freezing air typically found near the North Pole, will once again move into the central and eastern states this week, bringing some of the coldest air of the win… [+6433 chars]",
  "companyTags": [
    "Nvidia",
    "Google"
  ],
  "highlightsIndex": [
    [
      1,
      5
    ],
    [
      7,
      10
    ]
  ]
}
```
**Curl Command:** `curl -X GET -H <api-key> http://feed-api.stockic.in/api/v2/detail/<news-id>`
