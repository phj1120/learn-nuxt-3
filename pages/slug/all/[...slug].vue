<template>
  <q-page padding>
    <div class="text-center q-py-xl">
      <div class="text-h1">404</div>
      <p class="text-subtitle1 q-mt-md">Not found page</p>
      <strong class="text-h6">slug</strong>
      <p class="text-subtitle2">
        {{ $route.params.slug }}
      </p>
      <q-btn stretch flat label="예시" to="/slug/all/hello/world" />
    </div>
  </q-page>
</template>
