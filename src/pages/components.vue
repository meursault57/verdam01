
<template>
<<<<<<< HEAD
  <div>
    <template>
    <q-input v-model='doopa'></q-input>
    </template>
  </div>
</template>
=======
<div>
  <q-btn v-ripple @click="doSomething2" label="Click!" />
  <q-icon name="alarm" />
  <div v-touch-pan="handler">...</div>
  <div v-touch-swipe="handler">...</div>
  <div v-ripple>Click me. I got ripples.</div>
</div>
</template>>
>>>>>>> b0624ee686ec6da145ee63b9ca0cc854fc967a1d

<script>

export default {
<<<<<<< HEAD
  data () {
    return {
      doopa: 'Cześć z komponentu lokalnego!'
    }
  }
}
</script>
=======
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
>>>>>>> b0624ee686ec6da145ee63b9ca0cc854fc967a1d
