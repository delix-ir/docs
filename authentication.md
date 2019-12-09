# Authentication

Delix API uses API keys to authenticate all actions. You can view, create and manage your account API keys in the dashboard.

All calls to the API endpoints must be done over HTTPS protocol, including one of your API keys in authorization bearer header. In following examples, `YOUR_API_KEY` indicates the placeholder:

{% tabs %}
{% tab title="HTTP" %}
```text
GET /method HTTP/1.1
Authorization: Bearer YOUR_API_KEY
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
Be sure to keep your API keys secure in either your development or production environment.
{% endhint %}



