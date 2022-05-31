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
