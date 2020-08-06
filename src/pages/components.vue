
<template>
  <div>
    <q-page padding>
      <q-input v-model="doopa" @keyup.space="handleKeyup" @click="alertMessage" />
      <q-btn @click="doopa=''">Clear.L</q-btn>
      <q-btn @click="clearMessage">Clear.M</q-btn>
      <h5 class="border-grey">{{ doopa }}</h5>
    </q-page>
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
    },
    handleKeyup (e) {
      console.log(e)
      // if (e.keyCode === 32) {
      this.clearMessage()
      // }
    },
    alertMessage () {
      alert(this.doopa)
    }
  }
}
</script>

<style>
h5 {
color: #3a243b  /* deep purple */
}
.border-grey {
  border: 1px solid grey;
}
</style>
