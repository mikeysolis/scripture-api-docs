---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - php
  - python

toc_footers:
  - <a href='#'>Check out our demos</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Scripture API
---

# Introduction

Welcome to the Scripture API. A fun little project I built to power the backend for a suite of mobile apps I'm creating. The API consists of the 'Standard' scripture library found in the Church of Jesus Christ of Latter-Day Saints. This includes the Old and New Testament from the King James version of the Bible, the Book of Mormon, Doctrine & Covenants and Pearl of Great Price.

These records are all part of the [public domain](https://en.wikipedia.org/wiki/Public_domain) and as such do not include the Topical Guide, Bible Dictionary, chapter headers, indexes, references and other content created later.

The API conforms to the JsonApi standard. Some feel the JsonApi standard is overly verbose and difficult to understand but I feel the predictability and flexibility it provides is well worth it here. This is an API that I may open up to others in the future and predictability and flexibility will be a great benefit to developers.

The data for this API comes from the [LDS Documentation Project](https://scriptures.nephi.org/).

# Authentication

> To authorize, use this code:

```javascript
// Using the native Fetch API
fetch('url_goes_here', {
  headers: {
    'Authorization': 'Bearer <api_key>',
  },
})

// Using the Axios package
axios.create({
  headers: {
    'Authorization': 'Bearer <api_key>',
  }
})
```

```php
// Using native PHP
$curl = curl_init('url_goes_here');

$header = array(
  "Authorization: Bearer <api_key>",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$response = $client->request('GET', 'url_goes_here', [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
    ],
]);
```

```python
import requests

headers = {"Authorization": "Bearer <api_key>"}

reponse = requests.get('url_goes_here', headers=headers)
```

> Replace < api_key > with your actual Key. We recommend retreiving it from the environment.

The Scripture API uses Keys to allow access. At this time API keys are not available to the public, however this may change in the future.

Scripture Api expects the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <api_key>`

<aside class="notice">
You must replace <code>&ltapi_key&gt</code> with your actual API key.
</aside>

#Headers

> When sending requests, use the Accept header:

```javascript
// Using the native Fetch API
fetch('url_goes_here', {
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  },
})

// Using the Axios package
axios.create({
  headers: {
    'Authorization': 'Bearer <api_key>',
    'Accept': 'application/vnd.api+json',
  }
})
```

```php
// Using native PHP
$curl = curl_init('url_goes_here');

$header = array(
  "Authorization: Bearer <api_key>",
  "Accept: application/vnd.api+json",
)

curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);

// Using Laravel
$response = $client->request('GET', 'url_goes_here', [
    'headers' => [
        'Authorization' => 'Bearer <api_key>',
        'Accept' => 'application/vnd.api+json',
    ],
]);
```

```python
import requests

headers = CaseInsensitiveDict()
headers["Authorization"] = "Bearer <api_key>"
headers["Accept"] = "application/vnd.api+json"

reponse = requests.get('url_goes_here', headers=headers)
```

> These examples show the Authorization and Accept headers together.

The Scripture API adheres to the JsonAPI format. As such, you must send the correct headers with each request.

To do this simply add the 'Accept' header to the request. The header must look like the following:

`Accept: application/vnd.api+json`

<aside class="notice">
This is easily done alongside the Authorization header mentioned in the previous section.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

