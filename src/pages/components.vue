
<template>
  <div>
    <q-input v-model='doopa'></q-input>
    <q-btn @click="doopa=''">Clear.L</q-btn>
    <q-btn @click="clearMessage">Clear.M</q-btn>
    <h5>{{ doopa }}</h5>
  </div>
</template>

<script>
export default {
  data () {
    return {
      doopa: 'Wpis do komponentu, konstruktor.'
    }
  },
  methods: {
    clearMessage () {
      this.doopa = ''
    }
  }
}
</script>

<style>
h5 {
color: purple
}
</style>
