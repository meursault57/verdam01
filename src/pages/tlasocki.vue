<template>
<div>
    <head>
        <title>Skład dla zwierzaków :: Vue.js</title>
    </head>
    <div>
      <header>
        <div class="self-center full-width no-outline">{{ sitename }}</div>
      </header>
    </div>
</div>
</template>

<script>
var APP_LOG_LIFECYCLE_EVENTS = true

export default {
  data () {
    return {
      sitename: 'Skład dla zwierzaków :: Vue.js',
      product: {
        id: 1001,
        title: 'Karma dla kota 10',
        description: '10 kg karmy <em>oprze</em>!',
        price: 6700,
        image: 'assets/images/product-fullsize.png'
      }
    }
  },

  computed: {

  },
  beforeCreate: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeCreate')
    }
  },
  created: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**created')
    }
  },
  beforeMount: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeMount')
    }
  },
  mounted: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**mounted')
    }
  },
  beforeUpdate: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeUpdate')
    }
  },
  updated: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**updated')
    }
  },
  beforeDestroy: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('**beforeDestroy')
    }
  },
  destroyed: function () {
    if (APP_LOG_LIFECYCLE_EVENTS) {
      console.log('***destroyed')
    }
  }
}
</script>
