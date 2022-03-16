dark-mode
===

[![CI](https://github.com/jaywcjlove/dark-mode/actions/workflows/ci.yml/badge.svg)](https://github.com/jaywcjlove/dark-mode/actions/workflows/ci.yml)
[![jsDelivr CDN](https://data.jsdelivr.com/v1/package/npm/@wcj/dark-mode/badge?style=rounded)](https://www.jsdelivr.com/package/npm/@wcj/dark-mode)
[![npm version](https://img.shields.io/npm/v/@wcj/dark-mode.svg)](https://www.npmjs.com/package/@wcj/dark-mode)
[![Open in unpkg](https://img.shields.io/badge/Open%20in-unpkg-blue)](https://uiwjs.github.io/npm-unpkg/#/pkg/@wcj/dark-mode/file/README.md)

A custom element that allows you to easily put a Dark Mode 🌒 toggle. so you can initially adhere to your users' preferences according to [`prefers-color-scheme`](https://drafts.csswg.org/mediaqueries-5/#prefers-color-scheme), but also allow them to (optionally permanently) override their system setting for just your site.

## Installation

Install from npm:

```bash
npm install --save @wcj/dark-mode
```

Or, alternatively, use a `<script defer>` tag (served from unpkg's CDN):

CDN: [UNPKG](https://unpkg.com/@wcj/dark-mode/dist/) | [jsDelivr](https://cdn.jsdelivr.net/npm/@wcj/dark-mode/) | [Githack](https://raw.githack.com/jaywcjlove/dark-mode/gh-pages/dark-mode.min.js) | [Statically](https://cdn.statically.io/gh/jaywcjlove/dark-mode/gh-pages/dark-mode.min.js)

```html
<script src="https://unpkg.com/@wcj/dark-mode" defer></script>
```

## Usage

There are two ways how you can use `<dark-mode>`:

```html
<dark-mode></dark-mode>
<dark-mode light="Dart" dark="Light"></dark-mode>
<dark-mode dark="Dark" light="Light" style="border: 1px solid red; font-size: 12px;"></dark-mode>
```

Use in [React](https://github.com/facebook/react):

```jsx
import React from 'react';
import '@wcj/dark-mode';

function Demo() {
  return (
    <div>
      <dark-mode light="Dart" dark="Light"></dark-mode>
    </div>
  );
}
```

Toggle in JavaScript: 

```js
const toggle = document.querySelector('dark-mode');
const button = document.createElement('button');
button.textContent = 'Change Theme';
button.onclick = () => {
  const theme = document.body.dataset.colorMode;
  // or => const theme = toggle.mode
  document.body.setAttribute('data-color-mode', theme === 'light' ? 'dark' : 'light');
}
document.body.appendChild(button);
// Listen for toggle changes
// and toggle the `dark` class accordingly.
document.addEventListener('colorschemechange', (e) => {
  console.log(`Color scheme changed to "${e.detail.colorScheme}" or "${toggle.mode}".`);
  button.textContent = toggle.mode === 'dark' ? 'Change Theme 🌞' : 'Change Theme 🌒';
});
```

## Properties

Properties can be set directly on the custom element at creation time, or dynamically via JavaScript.

```typescript
export type ColorScheme = 'light' | 'dark';
export type ColorSchemeChangeEvent = CustomEvent<{ colorScheme: ColorScheme }>;
export class DarkMode extends HTMLElement {
  mode?: ColorScheme;
  dark?: string;
  light?: string;
  style?: React.CSSProperties;
}
```

## Contributors

As always, thanks to our amazing contributors!

<a href="https://github.com/jaywcjlove/dark-mode/graphs/contributors">
  <img src="https://jaywcjlove.github.io/dark-mode/CONTRIBUTORS.svg" />
</a>

Made with [github-action-contributors](https://github.com/jaywcjlove/github-action-contributors).

## License

Licensed under the [MIT License](https://opensource.org/licenses/MIT).
