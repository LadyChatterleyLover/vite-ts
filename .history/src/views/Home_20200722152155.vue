<template>
  <div>
    <h1>{{name}} --- {{num}}</h1>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue'
interface IState {
  name: string,
  age: number
}
export default defineComponent({
  setup() {
    let state: IState = reactive<IState>({
      name: 'jack',
      age: 20
    })
    return {
      ...toRefs(state)
    };
  },
});
</script>