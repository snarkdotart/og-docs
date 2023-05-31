---
icon: file
---


# Web hooks

You can define web hook URL using request data in `render_options` field

```json
{
    "collection_id": "******",
    "input_data": {"key": "value"},
    "render_options": {
        "callback_urls": ["http://example.com/api/callback/"]
    }
}
```

You can define multiple URLs:

```json
{
"render_options": {
        "callback_urls": [
            "http://example1.com/api/callback/",
            "http://example2.com/api/callback/"
        ]
  }
}
```

You can define a dict instead a string to define more details:

```json
{
    "render_options": {
        "callback_urls": [
            {
                "url":"http://example.com/api/callback/",
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
