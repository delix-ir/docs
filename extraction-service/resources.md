# Resources

## FileIdentifier

Lets services know which files and pages must be processed.

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
        <p><b>uuid</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">UUID of stored file</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><em>(optional)</em>
        </p>
        <p><b>page<br /></b><em>string</em>
        </p>
      </td>
      <td style="text-align:left">
        <p>Page range (<code>3-16</code>) or individual pages (<code>1,4,15</code>).</p>
        <p>For image extraction, this field is not needed.</p>
        <p>For document extraction, leaving it empty means all pages.</p>
      </td>
    </tr>
  </tbody>
</table>## ProcessedSyncExtract

The response of an extraction request that has been done synchronize.

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
        <p><b>uuid</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Unique identifier of the extraction request</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>status</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Currently always <code>processed</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>file_type</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Either <code>images</code> for image extraction service or <code>documents</code> for
        document extraction service.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>engine</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Engine name specified in the request. For example: <code>danlin</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>language</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Language code specified in the request. Can be null for <code>probe</code> engine.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>total_files</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Total number of files in the request.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>total_file_pages</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Total number of pages in actual files.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>total_processing_pages</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Total number of requested pages.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>initial_cost</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Cost of the extraction request.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>failed_pages</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Number of pages which couldn&apos;t be processed successfully.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>returned_credits</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Amount of credits returned to your account due to failed pages.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>files</b>
        </p>
        <p><em>AsyncExtractFile[]</em>
        </p>
      </td>
      <td style="text-align:left">An array of AsyncExtractFile which includes actual output.</td>
    </tr>
  </tbody>
</table>## AsyncExtractPage

This object represent output of processed pages from an actual source file.

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
        <p><b>uuid</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">UUID of related stored file.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>pages</b>
        </p>
        <p><em>ExtractFilePage[]</em>
        </p>
      </td>
      <td style="text-align:left"><em>Array of ExtractFilePage which keeps the output text.</em>
      </td>
    </tr>
  </tbody>
</table>## ExtractFilePage

This object includes a single output page details.

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
        <p><b>number</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">Indicates related page number in the stored file.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>status</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">Either <code>processed</code> or <code>failed</code> (with returned credits)</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>text</b>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">
        <p>Extracted text of the page.</p>
        <p><em>This field will be trimmed if status is marked as failed.</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

