# Quick Start

## Get your API keys

Your API requests are authenticated using API keys. Any request that doesn't include an API key will return an error.

You can generate an API key from your Dashboard at any time.

## Install the library

The best way to interact with our API is to use  fetch requests:

{% tabs %}
{% tab title="Node" %}
```
# Install via NPM
npm install axios 
```
{% endtab %}

{% tab title="Python" %}
```
# Install via pip
pip install requests
#OR
pip install httpclient
```
{% endtab %}
{% endtabs %}

## Make your first request

To make your first request, send an authenticated request to the Procom endpoint.

{% swagger baseUrl="https://api.myapi.com/v1" method="post" path="/pet" summary="Create pet." %}
{% swagger-description %}
Creates a new pet.
{% endswagger-description %}

{% swagger-parameter in="body" name="name" required="true" type="string" %}
The name of the pet
{% endswagger-parameter %}

{% swagger-parameter in="body" name="owner_id" required="false" type="string" %}
The 

`id`

 of the user who owns the pet
{% endswagger-parameter %}

{% swagger-parameter in="body" name="species" required="false" type="string" %}
The species of the pet
{% endswagger-parameter %}

{% swagger-parameter in="body" name="breed" required="false" type="string" %}
The breed of the pet
{% endswagger-parameter %}

{% swagger-response status="200" description="Pet successfully created" %}
```javascript
{
    "name"="Wilson",
    "owner": {
        "id": "sha7891bikojbkreuy",
        "name": "Samuel Passet",
    "species": "Dog",}
    "breed": "Golden Retriever",
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using our official libraries, or via `curl`:

{% tabs %}
{% tab title="Curl" %}
```clike
// Some code
curl -X GET \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  https://api.example.com/data

```
{% endtab %}

{% tab title="Node" %}
```javascript
// Import Axios library
const axios = require('axios');

// Define API endpoint URL
const endpoint = 'https://example.com/api';

// Define request parameters
const params = {
  param1: 'value1',
  param2: 'value2'
};

// Define request headers
const headers = {
  'Content-Type': 'application/json',
  'Authorization': 'Bearer ' + YOUR_API_KEY
};

// Make a GET request
axios.get(endpoint, {params, headers})
  .then(response => {
    console.log(response.data);
  })
  .catch(error => {
    console.log(error);
  });


```
{% endtab %}

{% tab title="Python" %}
```python
// Set your API key before making the request
import requests

# Set up the API endpoint and parameters
url = "https://api.example.com/data"
params = {"param1": "value1", "param2": "value2"}

# Make the API request
response = requests.get(url, params=params)

# Check the response status code
if response.status_code == 200:
    # Print the response content
    print(response.json())
else:
    print("Error: API request failed with status code", response.status_code)

```
{% endtab %}
{% endtabs %}
