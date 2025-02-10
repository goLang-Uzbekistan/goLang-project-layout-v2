### 1. Test GET /albums
This route should retrieve all albums. Here's how you can test it using cURL:

```bash
curl -X GET "http://localhost:8080/albums"
```

### 2. Test GET /albums/:id
This route should retrieve a specific album by its ID. Replace `:id` with the actual album ID you want to retrieve. For example, if you want to get the album with ID `1`, the command would look like this:

```bash
curl -X GET "http://localhost:8080/albums/1"
```
