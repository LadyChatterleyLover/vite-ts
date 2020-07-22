<template>
  <div>
    <h1>{{num}}</h1>
    <h1>{store.state.title}</h1>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  setup() {
    return {
      num: 10,
    };
  },
});
</script>