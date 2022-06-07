# Volumes

## Get All Volumes

> A basic request with no query parameters

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/volumes';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/volumes';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/volumes';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/volumes';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/volumes'

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
      "type": "volumes",
      "id": "3",
      "attributes": {
        "volumeTitle": "Book of Mormon",
        "volumeLongTitle": "The Book of Mormon",
        "volumeSubtitle": "Another Testament of Jesus Christ",
        "volumeShortTitle": "BoM",
        "volumeLdsUrl": "bofm"
      },
      "relationships": {
        "books": {
          "links": {
            "related": "http://example.com/api/v1/volumes/3/books",
            "self": "http://example.com/api/v1/volumes/3/relationships/books"
          }
        }
      },
      "links": {
        "self": "http://example.com/api/v1/volumes/3"
      }
    },
    // additional volumes
  ]
}
```

This endpoint retrieves all volumes. It also includes a optional relationship to an associated Books resource.

### HTTP Request

`GET http://example.com/api/v1/volumes`

### Query Parameters

All query parameters on the Volumes endpoint are optional.

Parameter | Default | Description
--------- | ------- | -----------
fields[type] | empty | Comma separated list of attributes and relationships to include
filter[attribute] | empty | Filter results based on an attribute

### Attributes

Name | Example
---------- | -------
volumeTitle | Book of Mormon
volumeLongTitle | The Book of Mormon
volumeSubtitle | Another Testament of Jesus Christ
volumeShortTitle | BoM
volumeLdsUrl | bofm

### Allowed Filters

Name | Description
---- | -----------
id | Allows the user to return a parial list of selected volumes.

`/api/v1/volumes?filter[id][]=1&filter[id][]=2` returns only the Old and New Testaments.

### Relationships

Type | Description
---- | ----
books | The list of books related to this volume

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>

## Get a Specific Volume

```javascript
// Using the native Fetch API
const url = 'http://example.com/api/v1/volumes/3';

fetch(url, {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
const url = 'http://example.com/api/v1/volumes/3';

await axios.get(url);
```

```php
// Using native PHP
$url = 'http://example.com/api/v1/volumes/3';
$curl = curl_init($url);

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$url = 'http://example.com/api/v1/volumes/3';

$response = $client->request('GET', $url, [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

url = 'http://example.com/api/v1/volumes/3'

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
    "self": "http://scripture-api.test/api/v1/volumes/3"
  },
  "data": {
    "type": "volumes",
    "id": "3",
    "attributes": {
      "volumeTitle": "Book of Mormon",
      "volumeLongTitle": "The Book of Mormon",
      "volumeSubtitle": "Another Testament of Jesus Christ",
      "volumeShortTitle": "BoM",
      "volumeLdsUrl": "bofm"
    },
    "relationships": {
      "books": {
        "links": {
          "related": "http://scripture-api.test/api/v1/volumes/3/books",
          "self": "http://scripture-api.test/api/v1/volumes/3/relationships/books"
        }
      }
    },
    "links": {
      "self": "http://scripture-api.test/api/v1/volumes/3"
    }
  }
}
```

This endpoint retrieves a specific volume. It includes an optional relationship to an associated Books resource. The Book data may be included directly onto the volume resource.

### HTTP Request

`GET http://example.com/api/v1/volumes/<ID>`

### URL Parameters

All query parameters on the Volumes endpoint are optional.

Parameter | Default | Description
--------- | ------- | -----------
fields[type] | empty | Comma separated list of attributes and relationships to include
include | empty | Include the associated relationship type and its data directly on the resource

### Attributes

Name | Example
---------- | -------
volumeTitle | Book of Mormon
volumeLongTitle | The Book of Mormon
volumeSubtitle | Another Testament of Jesus Christ
volumeShortTitle | BoM
volumeLdsUrl | bofm

### Includable Resources

Type | Description
---- | -----------
books | The books of scripture related to the requested volume.

`/api/v1/volumes/1?include=books` includes the books data directly on the volume resource.

### Relationships

Type | Description
---- | ----
books | The list of books related to this volume

<aside class="notice">
To read more about relationships, includes, filtering or selecting specific fields please refer their individual sections later in this documentation.
</aside>
