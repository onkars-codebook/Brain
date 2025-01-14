### Query Parameters

`GET: https://some-api.com/photos?orientation=landscape`

- here the `?orientation=landscape` is the query parameters

| Path Variable                                                                     | Query Parameters                                                   |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Located directly ___ after a slash___ in the path. It can be anywhere on the path | Located only at the end of a path, right after a question mark `?` |
| Accepts dynamic values                                                            | Accepts defined query keys with potentially `dynamic values`       |
| Often used for ` IDs` or entity names                                             | Often used for `options and filters`                               |
| **Example**: `/books/abc123` , and  e.g : `book/:id` to define the route          | **Example**: `/books?search=borges&checkedOut=false`               |

![[Query Parameters.png]]

