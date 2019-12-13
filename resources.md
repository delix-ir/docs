# Resources

## ErrorEnum

<table>
  <thead>
    <tr>
      <th style="text-align:left">Value</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MALFORMED_FILE</td>
      <td style="text-align:left">Uploaded file is either damaged or not supported</td>
    </tr>
    <tr>
      <td style="text-align:left">PAGE_COUNT_LIMIT_EXCEEDED</td>
      <td style="text-align:left">PDF file as more pages than what specified in this document</td>
    </tr>
    <tr>
      <td style="text-align:left">DUPLICATED_FILE</td>
      <td style="text-align:left">There are duplicated file identifiers in request body.</td>
    </tr>
    <tr>
      <td style="text-align:left">EXCEEDING_FILE_PAGE</td>
      <td style="text-align:left">
        <p>Total number of specified pages are exceeding service page limit.</p>
        <p>For example, sync extractions are limited to 5 pages per request.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">BAD_INPUT</td>
      <td style="text-align:left">File couldn&apos;t be processed. No more details are available.</td>
    </tr>
    <tr>
      <td style="text-align:left">GENERAL_EXCEPTION</td>
      <td style="text-align:left">The request has been failed unexpectedly. We&apos;ll investigate about
        it.</td>
    </tr>
    <tr>
      <td style="text-align:left">INVALID_FILE_PAGE</td>
      <td style="text-align:left">Specified page range is not valid for the actual stored file.</td>
    </tr>
    <tr>
      <td style="text-align:left">NO_SUFFICIENT_CREDITS</td>
      <td style="text-align:left">Your have no sufficient credits to perform the action.</td>
    </tr>
    <tr>
      <td style="text-align:left">STORAGE_COUNT_EXCEEDED</td>
      <td style="text-align:left">
        <p>You can&apos;t store more files due to exceeding number of files which
          is currently 30.</p>
        <p>You can delete previous files.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">STORAGE_SIZE_EXCEEDED</td>
      <td style="text-align:left">
        <p>You can&apos;t store more files due to exceeding size of your storage
          which is currently 100 MB.</p>
        <p>You can delete previous files.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">UNKNOWN_FIELD</td>
      <td style="text-align:left">The request contains unknown fields.</td>
    </tr>
    <tr>
      <td style="text-align:left">WRONG_FILE_TYPE</td>
      <td style="text-align:left">Related service doesn&apos;t support given file type. For example, you
        can&apos;t request PDF file extraction in <code>v1/image-extraction</code> endpoint.</td>
    </tr>
    <tr>
      <td style="text-align:left">FILE_UNDER_PROCESSING</td>
      <td style="text-align:left">File is under processing by one of the services and can&apos;t be deleted.</td>
    </tr>
  </tbody>
</table>

