# Actions API V2 Overview
Actions were introducted in the V2 of Stockic API, offering bookmarking of articles, performing integrations, etc. 

- **Endpoints**: The base endpoint is `http://actions.stockic.in/api/v2/actions`
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
  "message": "pong"
}
```
**Curl Command:** `curl -X GET -H <api-key> http://actions.stockic.in/api/v2/actions/ping`

---

## Add Bookmarks

This endpoint allows you to add bookmark to user's account. Since all the users are associated and completely identified with their API Keys, you can add news via their StockicID into their account.

**Request**
```bash
POST /actions/bookmarks-add
```

**Body**
```json
{
  "NewsID": "string"
}
```
The NewsID is equivalent to StockicID of the news and should be sent as a string data type.

**Response**
```json
{
  "message": "Bookmark added successfully"
}
```

**Curl Command:** `curl -X POST -H "X-API-Key: <user-api-key>" -d '{"NewsID": "<news-id>"}' http://actions.stockic.in/api/v2/actions/bookmarks-add`

---

## Remove Bookmarks

This endpoint allows you to remove bookmark from user's accourt. Since all the users are associated and completely identified with their API Keys, you can add news via their StockicID into their account. 

**Request**
```bash
DELETE /actions/bookmarks-remove
```

**Body** 
```json
{
  "NewsID": "string"
}
```
The NewsID is equivalent to StockicID of the news and should be sent as a string data type.

**Response**
```json
{
  "message": "Bookmark deleted successfully"
}
```

**Curl Command:** `curl -X DELETE -H "X-API-Key: <user-api-key>" -d '{"NewsID": "<news-id>"}' http://actions.stockic.in/api/v2/actions/bookmarks-remove`

--- 

## List Bookmarks

This endpoint allows you to list all the bookmarks user have. Since all the users are associated and completely identified with their API Keys, you can add news via their StockicID into their account.

**Request**
```bash
GET /actions/bookmarks-list
```

**Response**
```json
{
  "Success": true,
  "Message": "Bookmarks retrieved successfully",
  "Bookmarks": [
    "news-id-1",
    "news-id-2",
    "news-id-3"
  ]
}
```
**Curl Command:** `curl -X GET -H "X-API-Key: <user-api-key>" http://actions.stockic.in/api/v2/actions/bookmarks-list`

---

## Notion Authentication

Initiates an authentication session for Notion OAuth, generating a session token and returning the Notion authorization URL with the token as the state parameter. The session token is stored in Redis for validation during the OAuth flow.

It retrieves the Notion OAuth URL from environment variables and appends a generated session token. If the URL is missing or an error occurs during session creation, an error response is returned.

```bash
GET /notion/oauth/auth-session
```

**Success Response**
```json
{
  "Success": true,
  "OauthURL": "https://api.notion.com/v1/oauth/authorize?client_id=your-client-id&state=session-token"
}
```

**Failure Response**
```json
{
  "Success": false,
  "OauthURL": "URL not found"
}
```

**Curl Command:** `curl -X GET -H "X-API-Key: <user-api-key>" http://actions.stockic.in/api/v2/notion/oauth/auth-session`
