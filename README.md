# Provet Cloud Design System - Vue example project

This template should help get you started developing with Vue 3 in Vite.

This repo is an example of using Vue 3 in Vite along with Provet Cloud Design System's Web Components.
TypeScript is used, but this is not a necessity for using Vue and Provet Cloud Design System together.

This repo can be forked as a starting point for new apps. However, you may wish to undertake the process yourself so that all dependencies are up to date, and you can choose which Vue features you would like to use. The commit history shows the steps taken to integrate Vue and Provet Cloud Design System. Those steps are described next.

## Setting up a project from scratch

First initialize a new Vue project. This will ask a series of questions, to determine your project name, and which vue features you would like to use:

```sh
npm init vue@latest
```

Follow any instructions printed in the terminal.

Next install Provet Cloud Design System dependencies:

```sh
npm install @provetcloud/web-components @provetcloud/css --save
```

When complete, open your editor and navigate to the `vite.config` file. You must [configure Vue to support web components](https://vuejs.org/guide/extras/web-components.html#using-custom-elements-in-vue):

```js
import vue from "@vitejs/plugin-vue";

export default {
  plugins: [
    vue({
      template: {
        compilerOptions: {
          // treat all tags with a dash as custom elements
          isCustomElement: (tag) => tag.includes("-"),
        },
      },
    }),
  ],
};
```

In your `main.js` or `main.ts` file, import the Provet Cloud Design System dependencies:

```js
// main.js
import { createApp } from "vue";
import App from "./App.vue";

import "@provetcloud/css";
import "@provetcloud/web-components";

createApp(App).mount("#app");
```

This will ensure Provet Cloud Design System styles are included in your app, and register all Web Components ready for use.

Optionally, add the types and editor integration by installing `@provetcloud/web-components-vue-types` and adding the following to your `tsconfig.app.json` in a TypeScript project, or `jsconfig.json` in a JavaScript project:

```json
{
  "compilerOptions": {
    "types": ["@provetcloud/web-components-vue-types"]
  }
}
```

Now everything is ready! In a component file (assuming use of Vue Single-File Components and the Composition API), you can start using Provet Cloud Design System:

```vue
<script setup>
import { ref } from "vue";

const name = ref("");
const count = ref(0);
</script>

<template>
  <provet-stack class="n-reset">
    <provet-input label="Your name" v-model="name"></provet-input>
    <p>{{ name }}</p>

    <provet-button variant="primary" @click="count++">
      Count: {{ count }}
    </provet-button>
  </provet-stack>
</template>
```

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

Clone this repo, then:

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```
