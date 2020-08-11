<template>
    <q-page padding>
      <ul>
        <li v-for="task in tasks" :key="task">{{ task }}</li>
      </ul>
    </q-page>
</template>

<script>
var APP_LOG_LIFECYCLE_EVENTS = true
export default {
  data () {
    return {
      tasks: ['Go to shop', 'Get bananas', 'Get apples']
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
</style>
