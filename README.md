# resolve-id-refs
This module exports a function that resolves a HTML [ID reference list] into an
array of elements. An ID reference list is a string in which one or more ids is
separated by whitespace (spaces, tabs, or line breaks). Whitespace at the
beginning and end of the string is trimmed, and any ID that is not found in the
document raises an error.

```js
var resolve = require('resolve-id-refs');
resolve('foo bar');
// => [
//   document.getElementById('foo'),
//   document.getElementById('bar')
// ]
```

## API

```
resolve(ids<String> [, document<Document|DocumentFragment>]) => Array<Element>
```

* The `ids` argument **must** be a string. Any other types will raise an error.
* The second (optional) argument, `document`, should be a [Document] or
  [DocumentFragment] instance. Because `DocumentFragment` does not provide a
  `getElementById()` method, we use `querySelector('[id="' + id + '"]')`.

[Document]: https://developer.mozilla.org/en-US/docs/Web/API/Document
[DocumentFragment]: https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment
