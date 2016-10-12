# resolve-id-refs
This module exports a function that resolves a HTML [ID reference list] into an
array of elements. An ID reference list is a string in which one or more ids is
[separated by whitespace][space-separated tokens]. Whitespace at the beginning
and end of the string is trimmed, and any ID that is not found in the document
raises an error.

```js
var resolve = require('resolve-id-refs');
resolve('foo bar');
// => [
//   document.getElementById('foo'),
//   document.getElementById('bar')
// ]
```

See [the tests](test/) for more info.

## API

```
resolve(ids<String> [, document<Document|DocumentFragment>]) => Array<Element>
```

* The `ids` argument **must** be a string. Any other types will raise an error.
* The second (optional) argument, `document`, should be a [Document] or
  [DocumentFragment] instance. Because `DocumentFragment` does not provide a
  `getElementById()` method, we use `querySelector('[id="' + id + '"]')`.

[ID reference list]: https://www.w3.org/TR/2010/WD-html-markup-20100624/datatypes.html#common.data.idrefs-def
[space-separated tokens]: https://www.w3.org/TR/2010/WD-html5-20100624/common-microsyntaxes.html#space-separated-tokens
[Document]: https://developer.mozilla.org/en-US/docs/Web/API/Document
[DocumentFragment]: https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment
