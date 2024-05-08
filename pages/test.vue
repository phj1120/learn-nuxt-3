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
  </div>
</template>

<script setup lang="ts">
const showModal = ref(false);
const showComponet = ref(false);
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
