<template>
  <div>
    <h1>{{state.name}} --- {{state.age}}</h1>
    <div>
      <input type="text" v-model='state.value'>
    </div>
    <div>
      <button @click="goTo">跳转</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive , watch} from 'vue'
import {useRouter, Router} from 'vue-router'


interface IState {
  name: string,
  age: number,
  value: string
}
export default defineComponent({
  setup() {
    let router: Router = useRouter()
    let state: IState = reactive<IState>({
      name: 'jack',
      age: 20,
      value: ''
    })

    let goTo = ():void => {
      router.push('/about')
    }

    watch(() => state.value, (val: string) => {
      console.log(val)
    })
    return {
      state,
      goTo
    }
  }
})
</script>