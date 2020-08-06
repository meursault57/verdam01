
<template>
  <div>
    <q-page padding>
      <q-input v-model="message" @keyup.space="handleKeyup" />
      <q-btn @click="message=''">Clear.L</q-btn>
      <q-btn @click="clearMessage">Clear.M</q-btn>
      <h5 class="border-grey" v-show="message.length">{{ message }}</h5>
    </q-page>
  </div>
</template>

<script>
export default {
  data () {
    return {
      message: 'Wpis do komponentu, konstruktor.'
    }
  },
  methods: {
    clearMessage () {
      this.message = ''
    },
    handleKeyup (e) {
      console.log(e)
      // if (e.keyCode === 32) {
      this.clearMessage()
      // }
    },
    alertMessage () {
      alert(this.message)
    }
  }
}
</script>

<style>
h5 {
color: #3d213e  /* deep purple */
}
.border-grey {
  border: 1px solid grey;
}
</style>
