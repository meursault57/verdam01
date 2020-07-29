<template>
<div>
  <q-btn v-ripple @click="doSomething2" label="Click!" />
  <q-icon name="alarm" />
  <div v-touch-pan="handler">...</div>
  <div v-touch-swipe="handler">...</div>
  <div v-ripple>Click me. I got ripples.</div>
</div>
</template>>

<script>

export default {
  methods: {
    doSomething1 () {
      alert('doopa')
    },
    doSomething2: function () {
      // alert('doopa')
      console.log('Doopa!')
    }
  }
}

</script>>
