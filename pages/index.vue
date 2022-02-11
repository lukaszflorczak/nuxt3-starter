<template>
  <div>
    <h1>Hello World!</h1>
  </div>
</template>

<script lang="ts" setup>
import { useNuxtApp } from '#app';

const { ssrContext } = useNuxtApp();

const { data, error } = await useAsyncData<Category>('test', () =>
  $fetch('http://jsonplaceholder.typicode.com/404')
);

if (error.value) {
  const err = new Error(`Page not found`);
  err.statusCode = 404;
  ssrContext.error = err;
}
</script>
