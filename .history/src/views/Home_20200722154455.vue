<template>
  <div>
    <h1>{{name}} --- {{age}}</h1>
    <div>
      <input type="text" v-model='state.value'>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, watch } from 'vue'
interface IState {
  name: string,
  age: number,
  value: ''
}
export default defineComponent({
  setup() {
    let state: IState = reactive<IState>({
      name: 'jack',
      age: 20,
      value: ''
    })
    // watch(() => state.value, (val: string) => {
    //   console.log(val)
    // })
    return {
      state
    };
  },
});
</script>