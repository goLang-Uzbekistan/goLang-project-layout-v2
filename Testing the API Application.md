# Testing the API Application
- Postman: https://www.postman.com/
- Insomnia: https://insomnia.rest/
- Swagger: https://swagger.io/
- OpenAPI: https://www.openapis.org/
- Stoplight: https://stoplight.io/
- Paw: https://paw.cloud/
- SoapUI: https://www.soapui.org/
- Restlet: https://restlet.com/

____________________________________________________
# Testing the API for terminal: cURL CRUD operations
## GET all musics
```bash
curl -s "http://localhost:3000/musics/"
```

# GET single music by id (URL-encode spaces)
```bash
curl -s "http://localhost:3000/musics/2" | jq
```

# POST create music (public)
public qilishi uchun faqat: `-H "Authorization: Bearer ${TOKEN}" \` ni olib tashlang. agar qoldirsangiz unda middleware ishlaydi.

```bash
curl -X POST "http://localhost:3000/musics" \
-H "Content-Type: application/json" \
-d '{
"title": "New Track 2025",
"artist": "kazuhaKew",
"genre": "electronic",
"duration": 245,
"release_date": "2025-03-27"
}'
```
_____________________________
## Middleware ga misil:
```bash
// Complete the admin routes
musicGroup.Post("/", middlewares.AdminOnly(), handlers.CreateMusic)
musicGroup.Delete("/:id", middlewares.AdminOnly(), handlers.DeleteMusic)
musicGroup.Put("/:id", middlewares.AdminOnly(), handlers.UpdateMusic)
```

## POST create music (admin)
```bash
curl -X POST "http://localhost:3000/musics" \
-H "Authorization: Bearer ${TOKEN}" \
-H "Content-Type: application/json" \
-d '{
"title": "New Track 2025",
"artist": "kazuhaKew",
"genre": "electronic",
"duration": 245,
"release_date": "2025-03-27"
}'
```

## PUT update music (admin)
```bash
curl -X PUT "http://localhost:3000/musics/42" \
-H "Authorization: Bearer ${TOKEN}" \
-H "Content-Type: application/json" \
-d '{
"title": "Updated Track",
"genre": "ambient"
}'
```

## DELETE music (admin)
```bash
curl -X DELETE "http://localhost:3000/musics/42" \
-H "Authorization: Bearer ${TOKEN}"
```

## Search with multiple parameters
```bash
curl -s "http://localhost:3000/musics/search?q=ambient&artist=kazuhaKew&from=2025-01-01" | jq
```

_____________________________________
## Testing the API for terminal: cURL
docs: https://www.codepedia.org/ama/how-to-test-a-rest-api-from-command-line-with-curl/
```bash
curl -I http://localhost:8000/api/healthChecker ## GET request
```

```bash
curl -i -X HEAD http://localhost:8000/api/healthChecker ## HEAD request
```

```bash
curl -X GET "http://localhost:8000/api/healthChecker" -H "accept: application/json" ## GET request
```

Agar siz uni yanada chiroyli ko'rsatishni istasangiz, `jq` tavsiya qilaman:
```bash
curl http://localhost:8000/api/healthChecker | jq . ## GET request
```

## Curl options
    -I or --head - fetch the headers only
    -i, --include - include the HTTP response headers in the output
    -X, --request - specify a custom request method to use when communicating with the HTTP server (GET, PUT, DELETE&)

