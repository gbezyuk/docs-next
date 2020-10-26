# Введение

:::info Информация
Новичок в Vue.js? Начать изучение лучше с [руководства](../introduction.md).
:::

This guide is primarily for users with prior Vue 2 experience who want to learn about the new features and changes in Vue 3. **This is not something you have to read from top to bottom before trying out Vue 3.** While it looks like a lot has changed, a lot of what you know and love about Vue is still the same; but we wanted to be as thorough as possible and provide detailed explanations and examples for every documented change.

- [Быстрый старт](#быстрыи-старт)
- [Важные новые возможности](#важные-новые-возможности)
- [Кардинальные изменения](#кардинальные-изменения)
- [Поддержка библиотек](#поддержка-библиотек)

## Обзор

<br>
<iframe src="https://player.vimeo.com/video/440868720" width="640" height="360" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

Start learning Vue 3 at [Vue Mastery](https://www.vuemastery.com/courses-path/vue3).

## Быстрый старт

- Via CDN: `<script src="https://unpkg.com/vue@next"></script>`
- In-browser playground on [Codepen](https://codepen.io/yyx990803/pen/OJNoaZL)
- In-browser Sandbox on [CodeSandbox](https://v3.vue.new)
- Scaffold via [Vite](https://github.com/vitejs/vite):

  ```bash
  npm init vite-app hello-vue3 # OR yarn create vite-app hello-vue3
  ```

- Scaffold via [vue-cli](https://cli.vuejs.org/ru/):

  ```bash
  npm install -g @vue/cli # OR yarn global add @vue/cli
  vue create hello-vue3
  # select vue 3 preset
  ```

## Важные новые возможности

Some of the new features to keep an eye on in Vue 3 include:

- [Composition API](../composition-api-introduction.md)
- [Teleport](../teleport.md)
- [Fragments](fragments.md)
- [Emits Component Option](../component-custom-events.md)
- [`createRenderer` API from `@vue/runtime-core`](https://github.com/vuejs/vue-next/tree/master/packages/runtime-core) to create custom renderers
- [SFC Composition API Syntax Sugar (`<script setup>`)](https://github.com/vuejs/rfcs/blob/sfc-improvements/active-rfcs/0000-sfc-script-setup.md) <Badge text="экспериментально" type="warning" />
- [SFC State-driven CSS Variables (`<style vars>`)](https://github.com/vuejs/rfcs/blob/sfc-improvements/active-rfcs/0000-sfc-style-variables.md) <Badge text="экспериментально" type="warning" />
- [SFC `<style scoped>` can now include global rules or rules that target only slotted content](https://github.com/vuejs/rfcs/blob/master/active-rfcs/0023-scoped-styles-changes.md)

## Кардинальные изменения

:::info Информация
We are still working on a dedicated Migration Build of Vue 3 with Vue 2 compatible behavior and runtime warnings of incompatible usage. If you are planning to migrate a non-trivial Vue 2 app, we strongly recommend waiting for the Migration Build for a smoother experience.
:::

The following consists a list of breaking changes from 2.x:

### Global API

- [Global Vue API is changed to use an application instance](global-api.md)
- [Global and internal APIs have been restructured to be tree-shakable](global-api-treeshaking.md)

### Template Directives

- [`v-model` usage on components has been reworked](v-model.md)
- [`key` usage on `<template v-for>` and non-`v-for` nodes has changed](key-attribute.md)
- [`v-if` and `v-for` precedence when used on the same element has changed](v-if-v-for.md)
- [`v-bind="object"` is now order-sensitive](v-bind.md)
- [`v-on:event.native` modifier has been removed](v-on-native-modifier-removed.md)
- [`ref` inside `v-for` no longer register an array of refs](array-refs.md)

### Components

- [Functional components can only be created using a plain function](functional-components.md)
- [`functional` attribute on single-file component (SFC) `<template>` and `functional` component option are deprecated](functional-components.md)
- [Async components now require `defineAsyncComponent` method to be created](async-components.md)
- [Component events should now be declared with the `emits` option](emits-option.md)

### Render Function

- [Render function API changed](render-function-api.md)
- [`$scopedSlots` property is removed and all slots are exposed via `$slots` as functions](slots-unification.md)
- [`$listeners` has been removed / merged into `$attrs`](listeners-removed.md)
- [`$attrs` now includes `class` and `style` attributes](attrs-includes-class-style.md)

### Custom Elements

- [Custom elements whitelisting is now performed during template compilation](custom-elements-interop.md)
- [Special `is` prop usage is restricted to the reserved `<component>` tag only](custom-elements-interop.md#customized-built-in-elements)

### Другие незначительные изменения

- The `destroyed` lifecycle option has been renamed to `unmounted`
- The `beforeDestroy` lifecycle option has been renamed to `beforeUnmount`
- [Props `default` factory function no longer has access to `this` context](props-default-this.md)
- [Custom directive API changed to align with component lifecycle](custom-directives.md)
- [The `data` option should always be declared as a function](data-option.md)
- [The `data` option from mixins is now merged shallowly](data-option.md#mixin-merge-behavior-change)
- [Attributes coercion strategy changed](attribute-coercion.md)
- [Some transition classes got a rename](transition.md)
- [When watching an array, the callback will only trigger when the array is replaced. If you need to trigger on mutation, the `deep` option must be specified.](watch.md)
- `<template>` tags with no special directives (`v-if/else-if/else`, `v-for`, or `v-slot`) are now treated as plain elements and will result in a native `<template>` element instead of rendering its inner content.
- In Vue 2.x, application root container's `outerHTML` is replaced with root component template (or eventually compiled to a template, if root component has no template/render option). Vue 3.x now uses application container's `innerHTML` instead - this means the container itself is no longer considered part of the template.

### Удалённые API

- [`keyCode` support as `v-on` modifiers](keycode-modifiers.md)
- [$on, $off and \$once instance methods](events-api.md)
- [Filters](filters.md)
- [Inline templates attributes](inline-template-attribute.md)
- `$destroy` instance method. Users should no longer manually manage the lifecycle of individual Vue components.

## Поддержка библиотек

All of our official libraries and tools now support Vue 3, but most of them are still in beta status and distributed under the `next` dist tag on npm. **We are planning to stabilize and switch all projects to use the `latest` dist tag by end of 2020.**

### Vue CLI

<a href="https://www.npmjs.com/package/@vue/cli" target="_blank" noopener noreferrer><img src="https://img.shields.io/npm/v/@vue/cli"></a>

As of v4.5.0, `vue-cli` now provides built-in option to choose Vue 3 preset when creating a new project. You can upgrade `vue-cli` and run `vue create` to create a Vue 3 project today.

- [Документация](https://cli.vuejs.org/ru/)
- [GitHub](https://github.com/vuejs/vue-cli)

### Vue Router

<a href="https://www.npmjs.com/package/vue-router/v/next" target="_blank" noopener noreferrer><img src="https://img.shields.io/npm/v/vue-router/next.svg"></a>

Vue Router 4.0 provides Vue 3 support and has a number of breaking changes of its own. Check out its [README](https://github.com/vuejs/vue-router-next#vue-router-next-) for full details.

- [GitHub](https://github.com/vuejs/vue-router-next)
- [RFCs](https://github.com/vuejs/rfcs/pulls?q=is%3Apr+is%3Amerged+label%3Arouter)

### Vuex

<a href="https://www.npmjs.com/package/vuex/v/next" target="_blank" noopener noreferrer><img src="https://img.shields.io/npm/v/vuex/next.svg"></a>

Vuex 4.0 provides Vue 3 support with largely the same API as 3.x. The only breaking change is [how the plugin is installed](https://github.com/vuejs/vuex/tree/4.0#breaking-changes).

- [GitHub](https://github.com/vuejs/vuex/tree/4.0)

### Расширение инструментов для разработчика

We are working on a new version of the Devtools with a new UI and refactored internals to support multiple Vue versions. The new version is currently in beta and only supports Vue 3 (for now). Vuex and Router integration is also work in progress.

- Для Chrome: [Установить из магазина приложений Chrome](https://chrome.google.com/webstore/detail/vuejs-devtools/ljjemllljcmogpfapbkkighbhhppjdbg?hl=en)

  - Примечание: the beta channel may conflict with the stable version of devtools so you may need to temporarily disable the stable version for the beta channel to work properly.

- Для Firefox: [Скачать подписанное расширение](https://github.com/vuejs/vue-devtools/releases/tag/v6.0.0-beta.2) (файл `.xpi` в Assets)

### Поддержка IDE

Рекомендуется использовать [VSCode](https://code.visualstudio.com/) с нашим официальным расширением [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur), которое обеспечивает IDE всестороннюю поддержку Vue 3.

### Другие проекты

| Проект                | npm                           | Репозиторий          |
| --------------------- | ----------------------------- | -------------------- |
| @vue/babel-plugin-jsx | [![rc][jsx-badge]][jsx-npm]   | [[GitHub][jsx-code]] |
| eslint-plugin-vue     | [![ga][epv-badge]][epv-npm]   | [[GitHub][epv-code]] |
| @vue/test-utils       | [![beta][vtu-badge]][vtu-npm] | [[GitHub][vtu-code]] |
| vue-class-component   | [![beta][vcc-badge]][vcc-npm] | [[GitHub][vcc-code]] |
| vue-loader            | [![beta][vl-badge]][vl-npm]   | [[GitHub][vl-code]]  |
| rollup-plugin-vue     | [![beta][rpv-badge]][rpv-npm] | [[GitHub][rpv-code]] |

[jsx-badge]: https://img.shields.io/npm/v/@vue/babel-plugin-jsx.svg
[jsx-npm]: https://www.npmjs.com/package/@vue/babel-plugin-jsx
[jsx-code]: https://github.com/vuejs/jsx-next
[vd-badge]: https://img.shields.io/npm/v/@vue/devtools/beta.svg
[vd-npm]: https://www.npmjs.com/package/@vue/devtools/v/beta
[vd-code]: https://github.com/vuejs/vue-devtools/tree/next
[epv-badge]: https://img.shields.io/npm/v/eslint-plugin-vue.svg
[epv-npm]: https://www.npmjs.com/package/eslint-plugin-vue
[epv-code]: https://github.com/vuejs/eslint-plugin-vue
[vtu-badge]: https://img.shields.io/npm/v/@vue/test-utils/next.svg
[vtu-npm]: https://www.npmjs.com/package/@vue/test-utils/v/next
[vtu-code]: https://github.com/vuejs/vue-test-utils-next
[jsx-badge]: https://img.shields.io/npm/v/@ant-design-vue/babel-plugin-jsx.svg
[jsx-npm]: https://www.npmjs.com/package/@ant-design-vue/babel-plugin-jsx
[jsx-code]: https://github.com/vueComponent/jsx
[vcc-badge]: https://img.shields.io/npm/v/vue-class-component/next.svg
[vcc-npm]: https://www.npmjs.com/package/vue-class-component/v/next
[vcc-code]: https://github.com/vuejs/vue-class-component/tree/next
[vl-badge]: https://img.shields.io/npm/v/vue-loader/next.svg
[vl-npm]: https://www.npmjs.com/package/vue-loader/v/next
[vl-code]: https://github.com/vuejs/vue-loader/tree/next
[rpv-badge]: https://img.shields.io/npm/v/rollup-plugin-vue/next.svg
[rpv-npm]: https://www.npmjs.com/package/rollup-plugin-vue/v/next
[rpv-code]: https://github.com/vuejs/rollup-plugin-vue/tree/next

:::info Информация
Для получения дополнительной информации о совместимости библиотек и плагинов с Vue 3, обязательно ознакомьтесь с [этим issue в awesome-vue](https://github.com/vuejs/awesome-vue/issues/3544).
:::
