# Books

## Get All Books

> A basic request with no query parameters

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/books?filter[volumeId]=3';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/books?filter[volumeId]=3';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/books?filter[volumeId]=3';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/books?filter[volumeId]=3';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/books?filter[volumeId]=3'

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
      "type": "books",
      "id": "67",
      "attributes": {
        "volumeId": 3,
        "bookTitle": "1 Nephi",
        "bookLongTitle": "The First Book of Nephi",
        "bookSubtitle": "His Reign and Ministry",
        "bookShortTitle": "1 Ne.",
        "bookLdsUrl": "1-ne"
      },
      "relationships": {
        "volume": {
          "links": {
            "related": "http://scripture-api.test/api/v1/books/67/volume",
            "self": "http://scripture-api.test/api/v1/books/67/relationships/volume"
          }
        },
        "chapters": {
          "links": {
            "related": "http://scripture-api.test/api/v1/books/67/chapters",
            "self": "http://scripture-api.test/api/v1/books/67/relationships/chapters"
          }
        }
      },
      "links": {
        "self": "http://scripture-api.test/api/v1/books/67"
      }
    },
    {
      "type": "books",
      "id": "68",
      "attributes": {
        "volumeId": 3,
        "bookTitle": "2 Nephi",
        "bookLongTitle": "The Second Book of Nephi",
        "bookSubtitle": "",
        "bookShortTitle": "2 Ne.",
        "bookLdsUrl": "2-ne"
      },
      "relationships": {
        "volume": {
          "links": {
            "related": "http://scripture-api.test/api/v1/books/68/volume",
            "self": "http://scripture-api.test/api/v1/books/68/relationships/volume"
          }
        },
        "chapters": {
          "links": {
            "related": "http://scripture-api.test/api/v1/books/68/chapters",
            "self": "http://scripture-api.test/api/v1/books/68/relationships/chapters"
          }
        }
      },
      "links": {
        "self": "http://scripture-api.test/api/v1/books/68"
      }
    },
    // additional books
  ]
}
```

This endpoint retrieves all books in a volume. It requires you to specifiy the volume using a query filter. By default the resource includes relationship links to the associated volume and chapters for each book returned. It is possible to include the volume relationship data directly onto the book resource.

### HTTP Request

`GET http://example.com/api/v1/books?filter[volumeId]=3`

### Query Parameters

The filter[volumeId] parameter is required, all other are optional.

Parameter | Default | Description
--------- | ------- | -----------
filter[attribute] | required | Filter results based on an attribute
fields[type] | empty | Comma separated list of attributes and relationships to include

### Attributes

Name | Example
---------- | -------
volumeId | 3
bookTitle | 1 Nephi
bookLongTitle | The First Book of Nephi
bookSubtitle | His Reign and Ministry
bookShortTitle | 1 Ne.
bookLdsUrl | 1-ne

### Allowed Filters

Name | Description
---- | -----------
volumeId | Required, allows the user to select all books from a selected volume.

`/api/v1/books?filter[volumeId]=3` returns all books in the Book of Mormon.

### Includable Resources

Type | Description
---- | -----------
volumes | The volume resource for the returned book resource.

`/api/v1/books?filter[volumeId]=3&include=volume` includes the books data directly on the volume resource.

### Relationships

Type | Description
---- | ----
volumes | Volume associated with the book
chapters | Chapters associated with the book

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>

## Get a Specific Book

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/books/77';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/books/77';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/books/77';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/books/77';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/books/77'

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
    "self": "http://scripture-api.test/api/v1/books/77"
  },
  "data": {
    "type": "books",
    "id": "77",
    "attributes": {
      "volumeId": 3,
      "bookTitle": "3 Nephi",
      "bookLongTitle": "The Third Book of Nephi",
      "bookSubtitle": "The Book of Nephi, the Son of Nephi, who was the Son of Helaman",
      "bookShortTitle": "3 Ne.",
      "bookLdsUrl": "3-ne"
    },
    "relationships": {
      "volume": {
        "links": {
          "related": "http://scripture-api.test/api/v1/books/77/volume",
          "self": "http://scripture-api.test/api/v1/books/77/relationships/volume"
        }
      },
      "chapters": {
        "links": {
          "related": "http://scripture-api.test/api/v1/books/77/chapters",
          "self": "http://scripture-api.test/api/v1/books/77/relationships/chapters"
        }
      }
    },
    "links": {
      "self": "http://scripture-api.test/api/v1/books/77"
    }
  }
}
```

This endpoint retrieves a specific book. It includes optional relationships to associated Volume and Chapters resources. Both the Volume and Chapter data may be included directly on the Book resource.

### HTTP Request

`GET http://example.com/books/<ID>`

### URL Parameters

All query parameters on the Volumes endpoint are optional.

Parameter | Default | Description
--------- | ------- | -----------
fields[type] | empty | Comma separated list of attributes and relationships to include
include | empty | Include the associated relationship types and their data directly on the resource

### Attributes

Name | Example
---------- | -------
volumeId | 3
bookTitle | 3 Nephi
bookLongTitle | The Third Book of Nephi
bookSubtitle | The Book of Nephi, the Son of Nephi, who was the Son of Helaman
bookShortTitle | 3 Ne.
bookLdsUrl | 3-ne

### Includable Resources

Type | Description
---- | -----------
volumes | The volume associated with the book
chapters | The chapters associated with the book

`/api/v1/books/<ID>?include=volume,chapters` includes both relationships data directly onto the book resource.

### Relationships

Type | Description
---- | ----
volumes | The associated volume for the book
chapters | The associated chapters for the book 

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>
