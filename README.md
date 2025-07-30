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

## Styling

The button's pretty opinionated in terms of how its styled; wholesale changed probably require you downloading the source, modifying the component and building.

There are, however, some CSS variables you can use to customise certain properties, detailed below with their default:

```css
:root {
  --copy-to-clipboard-background-position: absolute;
  --copy-to-clipboard-background-position-right: 0.5rem;
  --copy-to-clipboard-background-position-top: 0.5rem;  
  --copy-to-clipboard-button-size: 1.5rem;        
  --copy-to-clipboard-background-color: #f9f9f9;  
  --copy-to-clipboard-border-radius: 3px;
}
