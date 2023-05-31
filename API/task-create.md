---
icon: file
---


# Submit new render task

- Make sure the required collection is created in the SRP database.
- Get the UUID of collection and save it.
- Get the API key from the administrator
- Submit new task using API

ENDPOINT: `https://srp.snark.art/api/v1/tasks`

HEADERS: `Authorization=Bearer <API-KEY>`

METHOD: `POST`

CONTENT TYPE: `application/json`

JSON DATA:

```json
{
"collection_id": "<UUID>",
"input_data": {"key": "value"}
}
```

### Example on Python

```python
import requests
data = {
        "collection_id": "<COLLECTION_UID>",
        "input_data": {
            "bg": "RareFlare3.png",
            "pants": "stepper",
            "pants_color": "#ffffff",
            "shoe_color": "#ff0000",
            "shoe": "4",
            "platform": "epic"
    }
}
headers = {'Authorization': 'Bearer <API_KEY>'}
requests.post('https://srp.snark.art/api/v1/tasks', json=data, headers=headers)
```
