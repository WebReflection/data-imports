# data-imports

<sup>**Social Media Photo by [Chris Lawton](https://unsplash.com/@chrislawton) on [Unsplash](https://unsplash.com/)**</sup>

An easy way to use modules without needing tools, published on `npm` to make it even simpler without needing *copy & paste*.

### Example
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  <script
    data-imports="uhtml,html-escaper"
    src="https://esm.run/data-imports"
  ></script>
  <!-- that's it -->
  <script type="module">
    import { render, html } from 'uhtml';
    render(document.body, html`It worked 🥳`);

    import { escape, unescape } from 'html-escaper';
    console.log(escape('<escaped>'));
  </script>
</head>
</html>
```

The `data-imports` field accepts comma separated entries that represent the module name.

By default the generated `importmap` will use the lovely [esm.run](https://esm.run/) service but if you need to directly serve some file it is possible to use a specialized syntax that will point directly to `cdn.jsdelivr.net/npm` instead:

```html
<script
  imports="@pyscript/core!/dist/core.js"
  src="https://esm.run/data-imports"
></script>
<script type="module">
  // will point at: https://cdn.jsdelivr.net/npm/@pyscript/core/dist/core.js
  import '@pyscript/core';
</script>
```

Any item with a `!` char will explicitly point at the specified path after such `!`, lovely handled by *jsdelivr* CDN.
