
<template>
    <q-page padding>
      <q-btn style= "position: absolute; right: 20px"> {{counter}} </q-btn>
      <q-input v-model="message" @keyup="handleKeyup" />
      <q-btn @click="message=''">Clear.L</q-btn>
      <q-btn @click="clearMessage">Clear.M</q-btn>
      <h5 v-if="message.length" class="border-grey">{{ message }}</h5>
      <h6 v-else>No message entered </h6>
      <hr>
      <p>Uppercase message: {{ messageUppercase () }}</p>
    </q-page>
</template>

<script>
export default {
  data () {
    return {
      message: 'Wpis do komponentu, konstruktor.',
      counter: 0
    }
  },
  methods: {
    clearMessage () {
      this.message = ''
    },
    handleKeyup (e) {
      console.log(e)
      if (e.keyCode === 32) {
        this.clearMessage()
      }
    },
    alertMessage () {
      alert(this.message)
    },
    messageUppercase () {
      return this.message.toUpperCase()
    }
  }
}
</script>

<style>
h5 {
  color: #3d213e;  /* deep purple */
}
h6 {
  color: red;
}
.border-grey {
  border: 1px solid grey;
}
</style>
