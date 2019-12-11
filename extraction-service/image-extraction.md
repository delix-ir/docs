---
description: Perform OCR on image files
---

# Image Extraction

Extracting images content process is synchronize which means the result of all OCRed pages will be available instantly in the response of the request.

Currently only 5 stored image files can be extracted in each request.

{% api-method method="get" host="https://api.delix.ir/v1" path="/image-extraction" %}
{% api-method-summary %}
Start Processing Images
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to start processing a bunch of image files.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="engine" type="object" required=true %}
OCR engine name an options specifier. See Engines for more info.
{% endapi-method-parameter %}

{% api-method-parameter name="files" type="array" required=true %}
Array of FileIdentifier with maximum of 5 items.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
Files are processed. The response in a ProcessedSyncExtract.
{% endapi-method-response-example-description %}

```
{
    'data': {
        'uuid': 'bd18e9f7-0186-406e-86c1-3aa0ddd72c01',
        'status': 'processed',
        'file_type': 'images',
        'engine': 'danlin',
        'language': 'fa',
        'total_files': 1
        'total_file_pages': 1
        'total_processing_pages': 1
        'initial_cost': 200,
        'failed_pages': 0,
        'returned_credits': 0,
        'files': [
            {
                'uuid': '123e4567-e89b-12d3-a456-426655440000',
                'pages': [
                    {
                        'number': 1,
                        'status': 'processed',
                        'text': 'سلام! این محتوای صفحه اوله'
                    }
                ]
            }
        ]
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



