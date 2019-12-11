# Resources

### StoredFile

File is in your storage and can be used to feed other services.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>uuid</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Unique identifier of the file. It&apos;s needed for other services</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>status</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Currently it&apos;s always `stored`</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>extension</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Extension of the uploaded file. For example: <code>pdf</code>, <code>png</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>page_count</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Number of pages in PDF file or 1 for images</td>
    </tr>
  </tbody>
</table>### RejectedFile

File is rejected during uploading process.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Field</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p><b>status</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Currently it&apos;s always <code>rejected</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>reason</b>
        </p>
        <p>&lt;em&gt;&lt;/em&gt;<a href="../errors.md"><em>FileError</em></a>&lt;em&gt;&lt;/em&gt;</p>
      </td>
      <td style="text-align:left">An error enum indicating why file has not been stored</td>
    </tr>
  </tbody>
</table>

