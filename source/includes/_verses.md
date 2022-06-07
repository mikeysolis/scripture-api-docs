# Verses

## Get All Verses

> A basic request with no query parameters

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/verses?filter[chapterId]=1160';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/verses?filter[chapterId]=1160';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/verses?filter[chapterId]=1160';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/verses?filter[chapterId]=1160';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/verses?filter[chapterId]=1160'

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
      "type": "verses",
      "id": "31103",
      "attributes": {
        "chapterId": 1190,
        "verseNumber": 1,
        "scriptureText": "I, Nephi, having been born of goodly parents, therefore I was taught somewhat in all the learning of my father; and having seen many afflictions in the course of my days, nevertheless, having been highly favored of the Lord in all my days; yea, having had a great knowledge of the goodness and the mysteries of God, therefore I make a record of my proceedings in my days."
      },
      "relationships": {
        "chapter": {
          "links": {
            "related": "http://scripture-api.test/api/v1/verses/31103/chapter",
            "self": "http://scripture-api.test/api/v1/verses/31103/relationships/chapter"
          }
        }
      },
      "links": {
        "self": "http://scripture-api.test/api/v1/verses/31103"
      }
    },
    {
      "type": "verses",
      "id": "31104",
      "attributes": {
        "chapterId": 1190,
        "verseNumber": 2,
        "scriptureText": "Yea, I make a record in the language of my father, which consists of the learning of the Jews and the language of the Egyptians."
      },
      "relationships": {
        "chapter": {
          "links": {
            "related": "http://scripture-api.test/api/v1/verses/31104/chapter",
            "self": "http://scripture-api.test/api/v1/verses/31104/relationships/chapter"
          }
        }
      },
      "links": {
        "self": "http://scripture-api.test/api/v1/verses/31104"
      }
    },
    // Additional verses
  ]
}
```

This endpoint retrieves all verses in a chapter. It requires you to specifiy the chapter using a query filter. By default the resource includes a relationship link to the associated chapter for each verse returned. It is possible to include the volume, book and chapter relationship data directly onto the verse resource.

### HTTP Request

`GET http://example.com/api/v1/verses?filter[chapterId]=1190`

### Query Parameters

The filter[chapterId] parameter is required, all others are optional.

Parameter | Default | Description
--------- | ------- | -----------
filter[attribute] | required | Filter results based on an attribute
fields[type] | empty | Comma separated list of attributes and relationships to include
include | empty | Include the associated relationship types and their data directly on the resource

### Attributes

Name | Example
---------- | -------
chapterId | 1190
verseNumber | 2
scriptureText | Yea, I make a record in the language of my father, which consists of the learning of the Jews and the language of the Egyptians.

### Allowed Filters

Name | Description
---- | -----------
chapterId | Required, allows the user to select all verses from a selected chapter.

`/api/v1/verses?filter[chapterId]=1190` returns all verses in 1st Nephi Chapter 1.

### Includable Resources

Type | Description
---- | -----------
volume | The related volume data for the returned verse resource.
book | The related book data for the returned verse resource.
chapter | The related chapter data for the returned verse resource.

`/api/v1/verses?filter[chapterId]=1190&include=chapter.book.volume` includes the volume, book, and chapter data directly on the verse resource.

### Relationships

Type | Description
---- | ----
volume | Volume associated with the verse
book | Book associated with the verse
chapter | Chapter associated with the chapter

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>

## Get a Specific Verse

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/verses/31103';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/verses/31103';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/verses/31103';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/verses/31103';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/verses/31103'

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
    "self": "http://scripture-api.test/api/v1/verses/31103"
  },
  "data": {
    "type": "verses",
    "id": "31103",
    "attributes": {
      "chapterId": 1190,
      "verseNumber": 1,
      "scriptureText": "I, Nephi, having been born of goodly parents, therefore I was taught somewhat in all the learning of my father; and having seen many afflictions in the course of my days, nevertheless, having been highly favored of the Lord in all my days; yea, having had a great knowledge of the goodness and the mysteries of God, therefore I make a record of my proceedings in my days."
    },
    "relationships": {
      "chapter": {
        "links": {
          "related": "http://scripture-api.test/api/v1/verses/31103/chapter",
          "self": "http://scripture-api.test/api/v1/verses/31103/relationships/chapter"
        }
      }
    },
    "links": {
      "self": "http://scripture-api.test/api/v1/verses/31103"
    }
  }
}
```

This endpoint retrieves a specific verse. It includes optional relationships to associated Volume, Book and Chapter resources. Both the Book and Verses data may be included directly on the Chapter resource.

### HTTP Request

`GET http://example.com/api/v1/verses/<ID>`

### URL Parameters

All query parameters on the Chapters endpoint are optional.

Parameter | Default | Description
--------- | ------- | -----------
fields[type] | empty | Comma separated list of attributes and relationships to include
include | empty | Include the associated relationship types and their data directly on the resource

### Attributes

Name | Example
---------- | -------
chapterId | 31103
verseNumber | 1
scriptureText | I, Nephi, having been born of goodly parents...

### Includable Resources

Type | Description
---- | -----------
volume | The related volume data for the returned verse resource.
book | The related book data for the returned verse resource.
chapter | The related chapter data for the returned verse resource.

`/api/v1/verses/<ID>?include=volume.book.chapters` includes all relationships data directly onto the verse resource.

### Relationships

Type | Description
---- | ----
volume | Volume associated with the verse
book | Book associated with the verse
chapter | Chapter associated with the chapter

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>
