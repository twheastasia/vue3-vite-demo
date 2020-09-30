<template>
  <div>
    <h1 @contextmenu="stopContextMenu">{{ msg }}</h1>
    <button @click="onAddCountClick">count is: {{ count }}</button>
    <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    noshow: String
  },
  setup(props) {
    const counter = ref(0)
    console.log(props)
    console.log(counter)
    console.log(counter.value)
    counter.value++
    console.log(counter)
    console.log(counter.value)
    return {}
  },
  data() {
    return {
      count: 10
    }
  },
  emits: {
    addCount: (count) => {
      return count > 2 ? true : false
    }
  },
  methods: {
    stopContextMenu(event) {
      event.preventDefault()
    },
    onAddCountClick() {
      this.count++
      this.$emit('addCount', this.count)
    }
  }
}
</script>
