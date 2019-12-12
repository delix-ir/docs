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
</table>## Extract

The response of an extraction request that has been finished.

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
      <td style="text-align:left">Either <code>processing</code> for queued (async) extracts or <code>processed</code> if
        it&apos;s been finished and results are available.</td>
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
      <td style="text-align:left">
        <p><em>(Will be available if extraction is done)<br /></em>
        </p>
        <p>Number of pages which couldn&apos;t be processed successfully.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>returned_credits</b>
        </p>
        <p><em>integer</em>
        </p>
      </td>
      <td style="text-align:left">
        <p><em>(Will be available if extraction is done)<br /></em>
        </p>
        <p>Amount of credits returned to your account due to failed pages.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>files</b>
        </p>
        <p><em>ExtractFile[]</em>
        </p>
      </td>
      <td style="text-align:left">
        <p><em>(Will be available if extraction is done)<br /></em>
        </p>
        <p>An array of ExtractFile which includes actual output or a link to them.</p>
      </td>
    </tr>
  </tbody>
</table>## ExtractFile

This object represent output of processed pages from an actual source file when execution is done.

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
        <p><em>ExtractFilePage[] or</em>
        </p>
        <p><em>string</em>
        </p>
      </td>
      <td style="text-align:left">
        <p>If the execution was synchronize, Array of ExtractFilePage which keeps
          the output text.</p>
        <p>If the execution was asynchronous, it&apos;ll be a URL to paginate results.</p>
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
</table>## PaginatedExtractFilePages

This object represents a full response of paginated async extraction result.

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
        <p><b>data</b>
        </p>
        <p>ExtractFilePage[]</p>
      </td>
      <td style="text-align:left">All file pages in current paginated result page.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>links</b>
        </p>
        <p>Read Description</p>
      </td>
      <td style="text-align:left">
        <p>Pagination links:</p>
        <p><b>first</b>: Link to first page</p>
        <p><b>last</b>: Link to last page</p>
        <p><b>next</b>: Link to next page or <code>null</code> if current page is the
          last one.</p>
        <p><b>prev</b>: Link to previous page or <code>null</code> if current page
          is the first one.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>meta</b>
        </p>
        <p>Read Description</p>
      </td>
      <td style="text-align:left">
        <p>Pagination details:</p>
        <p><b>current_page</b>: Number of current page in <code>page</code> query parameter.
          <br
          /><b>path</b>: Contains base pagination URL without <code>page</code> query.
          <br
          /><b>per_page</b>: Maximum number of available file page in each pagination
          page.</p>
        <p><b>total</b>: Total number of items in entire pagination.
          <br /><b>last_page</b>: Number of last possible pagination page.</p>
        <p><b>from</b>: Starting point of current page items in entire pagination.</p>
        <p><b>to</b>: End point of current page items in entire pagination.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>