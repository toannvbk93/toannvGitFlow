# SearchOption

Represents a search condition.

## Schema

```text
type SearchOption {
  target : SearchTarget
  isSafeSearch : boolean!
}
```

## Params

| Name | Type | Description | Note |
| --- | --- | --- | --- |
| target | SearchTarget | Represents a target to which the keyword is applied. | - |
| isSafeSearch | Boolean! | Represents whether a safe search is performed or not. | - |

