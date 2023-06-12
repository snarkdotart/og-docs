---
icon: file
---

# Uploading assets for SRP collection

Uploading process must be done in several steps

1. Prepare you assets as ZIP archive. Please make sure that the root of the archive is the root of the resource directory.
Do not create unnecessary nested levels.

2. Get upload URL 

ENDPOINT: `/api/v1/tasks/get_asset_upload_url/?collection_uid=<COLLECTION_ID>`

HEADERS: `Authorization=Bearer <API-KEY>`

METHOD: `GET`

RESPONSE:
```json
{
  "upload_url": "str",
  "content_type": "str",
  "id": "str"
}
```

3. Now you can upload your archive using `upload_url` and `PUT` method.
Be sure to use the specified content type!

4. Notify the server when the upload is complete

ENDPOINT: `/api/v1/tasks/create_asset/`

HEADERS: `Authorization=Bearer <API-KEY>`

METHOD: `POST`

CONTENT TYPE: `application/json`

REQUEST DATA:
```json
{
  "id": "<asset_id>" 
}

```

RESPONSE:
```json
{
  "upload_url": "str",
  "content_type": "str",
  "id": "str"
}
```

### JavaScript Example

```js
function upload_asset()
{
    const collection_id = $("#collection-id").val()
    let get_upload_url_endpoint = `/api/v1/tasks/get_asset_upload_url/?collection_uid=${collection_id}`
    $.ajax({
        url : get_upload_url_endpoint,
        type: "GET",
        headers: {
            "X-CSRFToken": getCookie("csrfmiddlewaretoken") // for Django view
        },
        xhrFields: {withCredentials: true},
        contentType: "application/json; charset=utf-8",
        dataType : "json",
        success: function( data ){
            const file = $("#asset-archive").prop('files')[0];
            let signedUrl = data['upload_url']
            const xhr = new XMLHttpRequest();
            xhr.open('PUT', signedUrl, true);
            xhr.setRequestHeader('Content-Type', data['content_type']);
            xhr.onload = function() {
              if (xhr.status === 200) {
                  alert(`Upload completed! Asset ID: ${data.id}`)
              } else {
                  console.error(xhr.statusText)
              }
            };
            xhr.upload.onprogress = (event) => {
                  const progress = Math.ceil(event.loaded / event.total)*100;
                  console.log(`Progress: ${progress}%`)
                };
            xhr.send(file);
        }
    });
}
```
### Python Example
```python
import requests

host = 'https://srp.snark.art/'  # staging URL
hd = {'Authorization': 'Bearer example'}
collection_id = 'example'
# get upload info
data = requests.get(f"{host}api/v1/tasks/get_asset_upload_url/?collection_uid={collection_id}", headers=hd).json()
# upload 
asset_file = 'example.zip'
requests.put(data['upload_url'], files={'file': open(asset_file, 'rb')}, headers={'content-type': data['content_type']})
# create asset
requests.post(f"{host}api/v1/tasks/create_asset/", headers=hd, json={'id': data['id']})
```
