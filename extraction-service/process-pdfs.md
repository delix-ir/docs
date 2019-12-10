# Engines

Currently there are three engines available to extract image and PDF contents with their own options.

## 📇 Danlin

Danlin is an OCR engine and is perfect for extracting content of images and PDFs with dense texts \(see example images: book pages, a column of newspaper\).

|  |  |
| :--- | :--- |
| Can be used for images? | ✅ |
| Can be used for scanned PDFs? | ✅ |
| Can be used for textual PDFs? | ✅ |

### Supported Options

Danlin _requires_ `language` field with one of these available languages which indicates primary language of the contents: `fa` \(Persian / Farsi\), `en` \(English\), `ar` \(Arabic\) and `tr` \(Turkish\).

### Example

Here is an example of requesting extraction service with Danlin engine:

```text
{
    'files': [ ... ],
    
    'engine': {
        'name': 'danlin',
        'options': {
            'language': 'fa'
        }
    }
}
```

## 📇 Tiho

Tiho is an OCR engine and is perfect for extracting content of images and PDFs with low dense texts \(see example images: book cover, product box\).

|  |  |
| :--- | :--- |
| Can be used for images? | ✅ |
| Can be used for scanned PDFs? | ✅ |
| Can be used for textual PDFs? | ✅ |

### Supported Options

Tiho _requires_ `language` field with one of these available languages which indicates primary language of the contents: `fa` \(Persian / Farsi\), `en` \(English\), `ar` \(Arabic\) and `tr` \(Turkish\).

### Example

Here is an example of requesting extraction service with Tiho engine:

```text
{
    'files': [ ... ],
    
    'engine': {
        'name': 'tiho',
        'options': {
            'language': 'fa'
        }
    }
}
```

## 📇 Probe

Probe is a binary analyzer engine which supports PDFs with embedded texts.

|  |  |
| :--- | :--- |
| Can be used for images? | ❌ |
| Can be used for scanned PDFs? | ❌ |
| Can be used for textual PDFs? | ✅ |

### Supported Options

Probe doesn't support any option.

### Example

Here is an example of requesting extraction service with Probe engine:

```text
{
    'files': [ ... ],
    
    'engine': {
        'name': 'probe'
    }
}
```



