# Chapters

## Get All Chapters

> A basic request with no query parameters

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/chapters?filter[bookId]=67';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/chapters?filter[bookId]=67';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/chapters?filter[bookId]=67';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/chapters?filter[bookId]=67';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/chapters?filter[bookId]=67'

headers = CaseInsensitiveDict()
headers["Authorization"] = "Bearer <api_key>"
headers["Accept"] = "application/vnd.api+json"

reponse = requests.get(url, headers=headers)
```

> The above command returns JSON structured like this:

```json
{
  "jsonapi": {
      "version": "1.0"
  },
  "data": [
    {
      "type": "chapters",
      "id": "1190",
      "attributes": {
        "bookId": 67,
        "chapterNumber": 1
      },
      "relationships": {
        "book": {
          "links": {
            "related": "http://scripture-api.test/api/v1/chapters/1190/book",
            "self": "http://scripture-api.test/api/v1/chapters/1190/relationships/book"
          }
        },
        "verses": {
          "links": {
            "related": "http://scripture-api.test/api/v1/chapters/1190/verses",
            "self": "http://scripture-api.test/api/v1/chapters/1190/relationships/verses"
          }
        }
      },
      "links": {
        "self": "http://scripture-api.test/api/v1/chapters/1190"
      }
    },
    {
      "type": "chapters",
      "id": "1191",
      "attributes": {
        "bookId": 67,
        "chapterNumber": 2
      },
      "relationships": {
        "book": {
          "links": {
            "related": "http://scripture-api.test/api/v1/chapters/1191/book",
            "self": "http://scripture-api.test/api/v1/chapters/1191/relationships/book"
          }
        },
        "verses": {
          "links": {
            "related": "http://scripture-api.test/api/v1/chapters/1191/verses",
            "self": "http://scripture-api.test/api/v1/chapters/1191/relationships/verses"
          }
        }
      },
      "links": {
        "self": "http://scripture-api.test/api/v1/chapters/1191"
      }
    },
    // Additional chapters
  ]
}
```

This endpoint retrieves all chapters in a book. It requires you to specifiy the book using a query filter. By default the resource includes relationship links to the associated book and verses for each chapter returned. It is possible to include the book relationship data directly onto the chapter resource.

### HTTP Request

`GET http://example.com/api/v1/chapters?filter[bookId]=67`

### Query Parameters

The filter[bookId] parameter is required, all others are optional.

Parameter | Default | Description
--------- | ------- | -----------
filter[attribute] | required | Filter results based on an attribute
fields[type] | empty | Comma separated list of attributes and relationships to include
include | empty | Include the associated relationship types and their data directly on the resource

### Attributes

Name | Example
---------- | -------
bookId | 67
chapterNumber | 1

### Allowed Filters

Name | Description
---- | -----------
bookId | Required, allows the user to select all chapters from a selected book.

`/api/v1/chapters?filter[bookId]=67` returns all chapters in 1st Nephi.

### Includable Resources

Type | Description
---- | -----------
book | The related book data for the returned chapter resource.

`/api/v1/chapters?filter[bookId]=67&include=book` includes the book data directly on the chapter resource.

### Relationships

Type | Description
---- | ----
book | Book associated with the chapter
verses | Verses associated with the chapter

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>

## Get a Specific Chapter

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/chapters/1190';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/chapters/1190';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/chapters/1190';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/chapters/1190';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/chapters/1190'

headers = CaseInsensitiveDict()
headers["Authorization"] = "Bearer <api_key>"
headers["Accept"] = "application/vnd.api+json"

reponse = requests.get(url, headers=headers)
```

> The above command returns JSON structured like this:

```json
{
  "jsonapi": {
    "version": "1.0"
  },
  "links": {
    "self": "http://scripture-api.test/api/v1/chapters/1190"
  },
  "data": {
    "type": "chapters",
    "id": "1190",
    "attributes": {
        "bookId": 67,
        "chapterNumber": 1
    },
    "relationships": {
      "book": {
        "links": {
          "related": "http://scripture-api.test/api/v1/chapters/1190/book",
          "self": "http://scripture-api.test/api/v1/chapters/1190/relationships/book"
        }
      },
      "verses": {
        "links": {
          "related": "http://scripture-api.test/api/v1/chapters/1190/verses",
          "self": "http://scripture-api.test/api/v1/chapters/1190/relationships/verses"
        }
      }
    },
    "links": {
      "self": "http://scripture-api.test/api/v1/chapters/1190"
    }
  }
}
```

This endpoint retrieves a specific chapter. It includes optional relationships to associated Book and Verses resources. Both the Book and Verses data may be included directly on the Chapter resource.

### HTTP Request

`GET http://example.com/api/v1/chapters/<ID>`

### URL Parameters

All query parameters on the Chapters endpoint are optional.

Parameter | Default | Description
--------- | ------- | -----------
fields[type] | empty | Comma separated list of attributes and relationships to include
include | empty | Include the associated relationship types and their data directly on the resource

### Attributes

Name | Example
---------- | -------
bookId | 67
chapterNumber | 3

### Includable Resources

Type | Description
---- | -----------
book | The related book data for the returned chapter resource.

`/api/v1/books/<ID>?include=volume,chapters` includes both relationships data directly onto the book resource.

### Relationships

Type | Description
---- | ----
book | Book associated with the chapter
verses | Verses associated with the chapter

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>
