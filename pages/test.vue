<template>
  <div>
    <p>TEST PAGE</p>
    <button @click="showModal = true">Show Modal</button>
    <my-modal v-if="showModal" @close="showModal = false">
      <template #header>
        <h3>custom header</h3>
      </template>
    </my-modal>
    <button @click="showComponet = !showComponet">Show Component</button>
    <my-component v-if="showComponet" />
    <div>
      <h5>MyComponent</h5>
      <component :is="MyComponent" />
      <h5>MyComponent2</h5>
      <component :is="MyComponent2" />
      <h5>selectedComponet</h5>
      <div>selected: {{ selected }}</div>
      <input
        id="MyComponent"
        v-model="selected"
        name="selectedComponet"
        type="radio"
        value="MyComponent"
      />
      <label for="MyComponent">MyComponent</label>
      <input
        id="MyComponent2"
        v-model="selected"
        name="selectedComponet"
        type="radio"
        value="MyComponent2"
      />
      <label for="selectedComponet2">MyComponent2</label>
      <component :is="selectedComponet" />
    </div>
  </div>
</template>

<script setup lang="ts">
import type { ConcreteComponent } from 'vue';
import { MyComponent2 } from '#components';

const showModal = ref(false);
const showComponet = ref(false);
const selected = ref('');
const selectedComponet: Ref<string | ConcreteComponent> = ref('');

watch(
  () => selected.value,
  (selected) => {
    selectedComponet.value = resolveComponent(selected);
  },
);

const MyComponent = resolveComponent('MyComponent');
</script>

<style scoped>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
