# Error Handling

You may face different error messages when you're working with the API. Here is a list of things you should consider when implementing it.

## Fetal Errors

They happen when one or more unexpected inputs found in your request. Here is how you should handle them:

Expected HTTP status code in the response: **422**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Attribute</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>message</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">A human readable message about the error.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>errors</b>
        </p>
        <p><em>array</em>
        </p>
      </td>
      <td style="text-align:left">
        <p><em>(when<code>error</code> field not presented)</em>
        </p>
        <p>An array of errors in which the key indicates a related field name and
          its value is an array of actual error text messages.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>error</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">
        <p><em>(when<code>errors</code> field not presented)</em>
        </p>
        <p>An ErrorEnum string which indicates the reason of failure when an input
          field is not necessarily concerned.</p>
      </td>
    </tr>
  </tbody>
</table>Here are two example of expected response:

{% tabs %}
{% tab title="With errors field" %}
```text
{
   'message': 'The given data was invalid.',
   'errors': {
      'engine': [
'تنظيمات موتور انتخابي صحيح نيست.'         
      ],
   }
}
```
{% endtab %}

{% tab title="With error field" %}
```text
{
   'message': 'فایل ارسالی دارای تعداد صفحات بیشتری از حداکثر تعیین شده است.',
   'error': 'PAGE_COUNT_LIMIT_EXCEEDED'
}
```
{% endtab %}
{% endtabs %}

## Acceptable Errors

Sometimes cancelling whole request is not needed. In these cases, no fetal error is thrown and instead, error is given in the expected response.

These kind of errors are method specific and are described in method descriptions.

For example, on storing new files, some of them may get rejected but not the whole request.

