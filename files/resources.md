# Resources

## StoredFile

File is in your storage and can be used to feed other services.

| Field | Type | Description |
| :--- | :--- | :--- |
| **uuid** | string | Unique identifier of the file. It's needed for other services |
| **status** | string | Currently it's always \`stored\` |
| **extension** | string | Extension of the uploaded file. For example: `pdf`, `png` |
| **page\_count** | integer | Number of pages in PDF file or 1 for images |

## RejectedFile

File is rejected during uploading process.

| Field | Type | Description |
| :--- | :--- | :--- |
| **status** | string | Currently it's always `rejected` |
| **reason** | [FileError](../error-handling/errors.md) | An error enum indicating why file has not been stored |





