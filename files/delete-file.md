# Delete File

If you're running out of your storage size, you can delete your desired files. Note that files will be deleted automatically after 24 hours of uploading time.

{% api-method method="delete" host="https://api.delix.ir/v1" path="/files/:uuid" %}
{% api-method-summary %}
Delete File
{% endapi-method-summary %}

{% api-method-description %}
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



