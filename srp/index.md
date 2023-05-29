# SRP Task API

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
"input_data": {...}
}
```

### Example on Python

```python
import requests
data = {
        "collection_id": "******",
        "input_data": {
            "bg": "RareFlare3.png",
            "pants": "stepper",
            "pants_color": "#ffffff",
            "shoe": "4",
            "shoe_color": "#ff0000",
            "platform": "epic"
    }
}
headers = {'Authorization': 'Bearer *****'}
requests.post('https://srp.snark.art/api/v1/tasks', json=data, headers=headers)
```

# Web hooks

You can define web hook URL using request data in `render_options` field

```json
data = {
    "collection_id": "******",
    "input_data": {...},
    "render_options": {
        "callback_urls": ["http://domain.com/api/callback/"]
    }
}
```

You can define multiple URLs:

```json
{
...
"render_options": {
        "callback_urls": [
            "http://domain1.com/api/callback/",
            "http://domain2.com/api/callback/"
        ]
  }
  ...
}
```

You can define a dict instead a string to define more details:

```json
{
    ...
    "render_options": {
        "callback_urls": [
            {
                "url":"http://domain.com/api/callback/",
                "method": "post",
                "headers": {"custom": "header"},
                "data": {"extra": "data"}
            }
        ]
    }			
}
```

Web hook data example:

```json
{
    "output_files": ["render/<COLLECTION_NAME>/<TASK_UUID>/render.png"],
    "status": "done",
    "task_id": "<TASK_UUID>",
    "timestamp": "2023-05-22T11:40:31.263Z"
}
```

The `output_files` field only exists if the status is `done`. Output file path is relative path on Google cloud storage. Full path is: `<BUCKET_NAME>/<RELATIVE_PATH>`

# Retrieve task status

To retrieve current task status:

ENDPOINT: `https://srp.snark.art/api/v1/tasks?id=<TASK_UID>`

HEADERS: `Authorization=Bearer <API-KEY>`

METHOD: `GET`

### Response example:

```json
{
  "id": "<TASK_UID>",
  "collection": {
    "name": "collection_name",
    "label": "Collection Name",
    "id": 1,
    "enabled": true,
    "tags": ["test"],
    "plugin": {
      "id": 1,
      "label": "Demo",
      "name": "demo"
    },
    "uid": "<COLLECTION_UID>",
    "options": {...}
  },
  "creation_date": "2023-05-12T18:27:38.662062Z",
  "status": "done",
  "enabled": true,
  "input_data": {...},
  "options": {
    "priority": 50,
    "callback_urls": ["https://domain.com/api/v1/render/callback"]
  },
  "created_by": {
    "id": 1,
    "name": "demo"
  },
  "tags": [
    "demo"
  ],
  "jobs": [
    1234
  ]
}
```
