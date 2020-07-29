<template>
<div>
  <q-btn @click="doSomething1" label="Click!" />
  <q-icon name="alarm" />
</div>
</template>>

<script>

export default {
  methods: {
    doSomething1 () {
      alert('doopa')
    },
    doSomething2: function () {
      alert('doopa')
    }
  }
}

</script>>
