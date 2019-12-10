# Managing Files

Both of OCR and PDF content extraction services require some files to be used. However, input files are being managed separately than the services.

This feature helps you to request multiple services on one or many files without uploading them in every request.

## Limitations

### Storage

You can have multiple files available at a time however, your storage have some limitations:

|  | Limitation |
| :--- | :--- |
| Max. stored file count | 30 |
| Max. total size of store | 100 MB |

You can send file deleting requests whenever you don't need the uploaded files anymore.

Files will be available for 24 hours and after that, will be deleted from your storage automatically.

### Supported Files

Currently you can upload these type of files: `pdf`, `png`, `jpg`, `jpeg`

|  | Limitation |
| :--- | :--- |
| Max. size of each image file | 2 MB |
| Max. size of each PDF file | 8 MB |
| Max. page count of each PDF file | 150 Pages |

{% api-method method="post" host="https://api.delix.ir/v1" path="/files" %}
{% api-method-summary %}
Upload New Files
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to upload files.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="file" type="array" required=true %}
An array of binary files. Only 5 files can be uploaded at each request.
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=207 %}
{% api-method-response-example-description %}
The response contains information about all uploaded files as an array of StoredFile and or RejectedFile. The response respects order of files in the request:
{% endapi-method-response-example-description %}

```
{
    'data': [
        {
            'uuid': '123e4567-e89b-12d3-a456-426655440000',
            'status': 'stored',
            'extension': 'pdf',
            'page_count': 7
        },
        {
            'status': 'rejected',
            'reason': 'PAGE_COUNT_LIMIT_EXCEEDED'
        },
        ...
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



{% api-method method="get" host="https://api.delix.ir/v1" path="/files" %}
{% api-method-summary %}
Get List of Files
{% endapi-method-summary %}

{% api-method-description %}
ows you to get index stored files which are available to be used.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.delix.ir/v1" path="/files/:uuid" %}
{% api-method-summary %}
Delete File
{% endapi-method-summary %}

{% api-method-description %}
If you're running out of your storage size, you can delete your desired files. Note that files will be deleted automatically after 24 hours of uploading time.  
This endpoint allows you to delete a stored file.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="uuid" type="string" %}
UUID of the stored file.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a related file or file is cleaned from your storage.
{% endapi-method-response-example-description %}

```
{}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Resources

### StoredFile

File is in your storage and can be used to feed other services.

| Field | Type | Description |
| :--- | :--- | :--- |
| **uuid** | string | Unique identifier of the file. It's needed for other services |
| **status** | string | Currently it's always \`stored\` |
| **extension** | string | Extension of the uploaded file. For example: `pdf`, `png` |
| **page\_count** | integer | Number of pages in PDF file or 1 for images |

### RejectedFile

File is rejected during uploading process.

| Field | Type | Description |
| :--- | :--- | :--- |
| **status** | string | Currently it's always `rejected` |
| **reason** | [FileError](../error-handling/errors.md) | An error enum indicating why file has not been stored |



