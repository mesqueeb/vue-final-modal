---
title: Recommended use
description: 'Vue Final Modal is a renderless, stackable, detachable and lightweight modal component.'
position: 3
category: Examples
---


## Write a `higher-order component`

<alert>

You can create a `higer-order component` easily and can customize `template`, `script` and `style` based on your needs.

</alert>

### VModal.vue

<show-code open>

```vue
<template>
  <vue-final-modal
    :value="value"
    v-bind="$attrs"
    classes="modal-container"
    content-class="modal-content"
    v-on="$listeners"
  >
    <button class="modal__close" @click="$emit('input', false)">
      <mdi-close></mdi-close>
    </button>
    <span class="modal__title">
      <slot name="title"></slot>
    </span>
    <div class="modal__content">
      <slot></slot>
    </div>
    <div class="modal__action">
      <button class="vfm-btn" @click="$emit('confirm')">confirm</button>
      <button class="vfm-btn" @click="$emit('cancel')">cancel</button>
    </div>
  </vue-final-modal>
</template>

<script>
export default {
  name: 'VModal',
  props: {
    value: { type: Boolean, default: false }
  }
}
</script>

<style scoped>
::v-deep .modal-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
::v-deep .modal-content {
  position: relative;
  display: flex;
  flex-direction: column;
  max-height: 90%;
  margin: 0 1rem;
  padding: 1rem;
  border: 1px solid #e2e8f0;
  border-radius: 0.25rem;
  background: #fff;
}
.modal__title {
  margin: 0 2rem 0 0;
  font-size: 1.5rem;
  font-weight: 700;
}
.modal__content {
  flex-grow: 1;
  overflow-y: auto;
}
.modal__action {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
  padding: 1rem 0 0;
}
.modal__close {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
}
</style>

<style scoped>
.dark-mode div::v-deep .modal-content {
  border-color: #2d3748;
  background-color: #1a202c;
}
</style>
```

</show-code>

## How to use the `higher-order component`

### Live example

<hoc-example></hoc-example>

<show-code open class="pt-4">

```vue
<template>
  <div>
    <v-modal v-model="show" @confirm="confirm" @cancel="cancel">
      <template v-slot:title>Hello, vue-final-modal</template>
      <p>
        Vue Final Modal is a renderless, stackable, detachable and lightweight
        modal component.
      </p>
    </v-modal>

    <button class="vfm-btn" @click="show = true">Open modal</button>
  </div>
</template>

<script>
export default {
  data: () => ({
    show: false
  }),
  methods: {
    confirm() {
      // some code...
      this.show = false
    },
    cancel() {
      // some code...
      this.show = false
    }
  }
}
</script>
```

</show-code>