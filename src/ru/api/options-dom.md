# DOM

## template

- **Тип:** `string`

- **Подробности:**

  A string template to be used as the markup for the component instance. The template will **replace** the mounted element. Any existing markup inside the mounted element will be ignored, unless content distribution slots are present in the template.

  If the string starts with `#` it will be used as a `querySelector` and use the selected element's innerHTML as the template string. This allows the use of the common `<script type="x-template">` trick to include templates.

  :::tip Примечание
  From a security perspective, you should only use Vue templates that you can trust. Never use user-generated content as your template.
  :::

  :::tip Примечание
  If render function is present in the Vue option, the template will be ignored.:::

- **См. также:**
  - [Lifecycle Diagram](../guide/instance.md#lifecycle-diagram)
  - [Content Distribution with Slots](../guide/component-basics.md#content-distribution-with-slots)

## render

- **Тип:** `Function`

- **Подробности:**

  An alternative to string templates allowing you to leverage the full programmatic power of JavaScript.

- **Использование:**

  ```html
  <div id="app" class="demo">
    <my-title blog-title="A Perfect Vue"></my-title>
  </div>
  ```

  ```js
  const app = Vue.createApp({})

  app.component('my-title', {
    render() {
      return Vue.h(
        'h1', // tag name,
        this.blogTitle // tag content
      )
    },
    props: {
      blogTitle: {
        type: String,
        required: true
      }
    }
  })

  app.mount('#app')
  ```

  :::tip Примечание
  The `render` function has priority over the render function compiled from `template` option or in-DOM HTML template of the mounting element
  :::

- **См. также:** [Render Functions](../guide/render-function.md)
