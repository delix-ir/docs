# Upload New Files

## Supported Files

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
The response contains information about all uploaded files whether they are successfully stored or rejected. See sections below for detailed response.  
Here is an example response for two uploaded files:
{% endapi-method-response-example-description %}

```
[
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
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Uploaded File Response

If corresponding file is stored successfully, the response will contain following object:

| Field | Type | Description |
| :--- | :--- | :--- |
| **uuid** | string | Unique identifier of the file. It's needed for other services |
| **status** | string | Currently it's always \`stored\` |
| **extension** | string | Extension of the uploaded file. For example: `pdf`, `png` |
| **page\_count** | integer | Number of pages in PDF file or 1 for images |

### Failed File Response

If corresponding file is failed to be stored, the response will contain following object:

| Field | Type | Description |
| :--- | :--- | :--- |
| **status** | string | Currently it's always `rejected` |
| **reason** | [FileError](../../error-handling/errors.md) | An error enum indicating why file has not been stored |



