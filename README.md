# Copy to Clipboard

A web component to copy some text to the clipboard. Written in Svelte.

## Usage

Import the file, ensuring you set the `type` to `module`:

```html
<script type="module" src="/dist/copy-to-clipboard.es.js"></script>		
```

Use it in your HTML like this:

```html
<copy-to-clipboard value="The text to copy"></copy-to-clipboard>
```

## Modifying It

The code for the component is in `src/wc/CopyToClipboard.wc.svelte`; everything else is for development purposes (e.g. `src/App.vue`) or building (e.g. `srr/wc/web-components.ts`).

To build it:

```bash
npm run dev
```

During development, run Vite with:

```bash
npm run dev
```