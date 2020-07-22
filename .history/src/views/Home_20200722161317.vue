<template>
  <div>
    <h1>{{state.name}} --- {{state.age}}</h1>
    <div>
      <input type="text" v-model='state.value'>
    </div>
    <div>
      <button @click="goTo">跳转</button>
    </div>
    <div>
      {{computedName}}
    </div>
    <div>
      {{store.state.title}}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive , watch, computed, ComputedRef} from 'vue'
import {useRouter, Router} from 'vue-router'
import {useStore, Store} from 'vuex'

interface IState {
  name: string,
  age: number,
  value: string
}
export default defineComponent({
  setup() {
    let router: Router = useRouter()
    let store:Store<{}> = useStore()

    let state: IState = reactive<IState>({
      name: 'jack',
      age: 20,
      value: ''
    })
    let computedName:ComputedRef<string> = computed(() => state.name + 'abc')
    let goTo = ():void => {
      router.push('/about')
    }

    watch((): string => state.value, (val: string) => {
      console.log(val)
    })
    return {
      state,
      goTo,
      computedName,
      store
    }
  }
})
</script>