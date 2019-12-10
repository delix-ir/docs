# List Files

{% api-method method="get" host="https://api.delix.ir/v1" path="/files" %}
{% api-method-summary %}
List Files
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get index stored files which are available to be used.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Files successfully retrieved as an array of StoredFile.
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
            'uuid': '7b75cdc1-7944-40eb-ac4b-6e23ca547ed4',
            'status': 'stored',
            'extension': 'jpeg',
            'page_count': 1
        },
        ...
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



