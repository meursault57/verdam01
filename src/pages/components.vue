
<template>
  <div>
    <q-input v-model='doopa'></q-input>
    <h5>{{ doopa }}</h5>
  </div>
</template>

<script>
export default {
  data () {
    return {
      doopa: 'Wpis do komponentu, konstruktor.'
    }
  }
}
</script>
