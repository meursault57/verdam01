
<template>
    <q-page padding>
      <q-btn style= "position: absolute; right: 20px" @click="counter1++"> {{counter1}} </q-btn>
      <q-btn style= "position: absolute; right: 70px" @click="counter2++"> {{counter2}} </q-btn>
      <input v-model="message" @keyup="handleKeyup" />
      <button @click="message=''">Clear.L</button>
      <button @click="clearMessage">Clear.M</button>
      <h5 v-if="message.length" class="border-grey">{{ message }}</h5>
      <h6 v-else>No message entered </h6>
      <hr>
      <!-- <p>Uppercase message: <b>{{ messageUppercase_1() }}</b></p> -->
      <p>Uppercase message: <b>{{ messageUppercase }}</b></p>
      <p>Lovercase message: <b>{{ message | messageLovercase }}</b></p>
    </q-page>
</template>

<script>
var APP_LOG_LIFECYCLE_EVENTS = true
export default {
  data () {
    return {
      message: 'Wpis z KonstruktorA.',
      counter1: 0,
      counter2: 0
    }
  },
  computed: {
    messageUppercase () {
      console.log('messageUppercase was fired')
      return this.message.toUpperCase()
    }
  },
  filters: {
    messageLovercase (value) {
      return value.toLowerCase()
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
    messageUppercase_1 () {
      console.log('messageUppercase_1 was fired')
      return this.message.toUpperCase()
    }
  },
  // LIFECYCLE_EVENTS ////////////////
  beforeCreate: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****beforeCreate')
    }
  },
  created: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****created')
    }
  },
  beforeMount: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****beforeMount')
    }
  },
  mounted: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****mounted')
    }
  },
  beforeUpdate: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****beforeUpdate')
    }
  },
  updated: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****updated')
    }
  },
  beforeDestroy: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****beforeDestroy')
    }
  },
  destroyed: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('*****destroyed')
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
