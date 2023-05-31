---
icon: file
---


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
    "options": {"key": "value"}
  },
  "creation_date": "2023-05-12T18:27:38.662062Z",
  "status": "done",
  "enabled": true,
  "input_data": {"key": "value"},
  "options": {
    "priority": 50,
    "callback_urls": ["https://example.com/api/render/callback"]
  },
  "output_files": [
    "render/collection_name/<TASK_UID>/filename1.ext",
    "render/collection_name/<TASK_UID>/filename2.ext"
  ],
  "created_by": {
    "id": 1,
    "name": "demo"
  },
  "tags": ["demo"],
  "jobs": [1234]
}
```
