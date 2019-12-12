# Extracting Text

## Image Extraction Methods

Extracting images content process is synchronize which means the result of all OCRed pages will be available instantly in the response of the request.

Currently only 5 stored image files can be extracted in each request.

{% api-method method="post" host="https://api.delix.ir/v1" path="/image-extraction" %}
{% api-method-summary %}
Process Images
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

## PDF Extraction Methods



Extracting PDF pages content can be done both synchronously and asynchronously.

By requesting synchronous execution, result will be available instantly but in a request, you're limited to 5 specified pages only.

In asynchronous execution however, you can specify up to 150 pages per PDF but the result won't be available in the response of the request. Instead, it'll be added to processing queue and can be accessed later via direct request or a callback URL which will be called after finishing processing.

Currently only 5 stored PDF files can extracted in each request.

{% api-method method="post" host="https://api.delix.ir/v1" path="/document-extraction" %}
{% api-method-summary %}
Process PDFs
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to start processing a bunch of PDF files.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="callback\_url" type="string" required=false %}
After finishing extraction, a POST request will be send to this URL with ExtractedCallbackData body.  
If not given, you need to use other endpoint to check the status of processing.
{% endapi-method-parameter %}

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
Files are processed. The response in a QueuedExtract.
{% endapi-method-response-example-description %}

```
{
    'data': {
        'uuid': 'bd18e9f7-0186-406e-86c1-3aa0ddd72c01',
        'status': 'processing',
        'file_type': 'documents',
        'engine': 'danlin',
        'language': 'fa',
        'total_files': 1,
        'total_file_pages': 72,
        'total_processing_pages': 10
        'initial_cost': 1000
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

{% api-method method="get" host="https://api.delix.ir/v1" path="/extracts/:extractUuid/files/:fileUuid/contents?page=:page" %}
{% api-method-summary %}
Paginate Results
{% endapi-method-summary %}

{% api-method-description %}
Paginate result of a file in finished asynchronous extraction.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="extractUuid" type="string" required=true %}
UUID of extract
{% endapi-method-parameter %}

{% api-method-parameter name="fileUuid" type="string" required=true %}
UUID of related stored file included in the extract request.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="page" type="number" required=true %}
Number of the result pagination page \(not file page\).
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
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

## Other Methods

{% api-method method="get" host="https://api.delix.ir/v1" path="/extracts/:uuid" %}
{% api-method-summary %}
Get Extract
{% endapi-method-summary %}

{% api-method-description %}
Use this endpoint to get extract details. You may call it when callback request is made or on a regular basis \(once every minute for example\) if callback URL is not used in initial extraction request.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="uuid" type="string" required=true %}
Extract UUID
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

