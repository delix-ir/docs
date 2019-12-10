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



