# SearchTarget

Represents the target to which the keyword is applied when searching for a title or book.

## Schema

```text
enum SearchTarget {
  title
  publisher
  explanation
  all
}
```

## Params

| Name | Description | Note |
| --- | --- | --- |
| title | Name of Title | - |
| publisher | Publisher name | - |
| explanation | Introduction text | - |
| all | All \(name, publisher name, introduction text\) | - |

