## Framer ESM Example Setup

This is an example how to set up a repository that builds code that can be consumed in Framer. It builds standard JavaScript into ES Modules that you can both use locally for development or to deploy to any http server for distribution.

- `yarn run serve` This runs a local web server with the built code.
- `yarn run build` This builds the code in `dist`.

## Features

- Built on `esbuild` for speed and to support JavaScript, TypeScript and JSX.
- Custom plugin to handle ESM imports and rewrite local import paths.
- CSS Modules plugin to support writing css scoped modules.
- GitHub Workflow to deploy versioned code on GitHub pages.

## Development

Start the development server with:

```
yarn run serve
```

Open Framer, create a code file and paste the following:

```.tsx
import { addPropertyControls, ControlType } from "framer"
import { Button as ImportedButton } from "http://127.0.0.1:8001/index.js"

export const Button: React.ComponentType = ImportedButton

addPropertyControls(Button, {
    title: {
        title: "Title",
        type: ControlType.String,
        defaultValue: "Title",
    },
    onTap: {
        type: ControlType.EventHandler,
    },
})
```

## Deployment

## CSS

You can use the default esbuild [css importer](https://esbuild.github.io/content-types/#css), or you can use a [plugin to use css modules](https://github.com/indooorsman/esbuild-css-modules-plugin), that optionally auto inserts the css as a `<style>` tag (as configured).
