<template>
    <q-page padding>
      <ul>
        <!--
        <li v-for="(task, key) in tasks" :key="key">
          <div>{{ task.name }} ({{ key }})</div>
          <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
          <button @click="deleteTask(key)">xy</button>
          </li>
        -->
      <task
      v-for="(task, key) in tasks" :key="key"></task>
      </ul>
    </q-page>
</template>

<script>
// import Task from 'components/Task.vue'
var APP_LOG_LIFECYCLE_EVENTS = true
export default {
  data () {
    return {
    /* tasks: ['Go to shop', 'Get bananas', 'Get apples', 'Get Kotelet'] */
      tasks: [
        {
          name: 'Go to shop',
          dueDate: '2019/05/12',
          dueTime: '18:30'
        },
        {
          name: 'Get bananas',
          dueDate: '2019/05/13',
          dueTime: '14:00'
        },
        {
          name: 'Get apples',
          dueDate: '2019/05/14',
          dueTime: '16:00'
        },
        {
          name: 'Get Kotelet',
          dueDate: '2019/05/15',
          dueTime: '18:00'
        }
      ]
    }
  },
  methods: {
    deleteTask (key) {
      console.log(key)
      this.tasks.splice(key, 1)
    }
  },
  components: {
    task: require('components/Task.vue').default
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
