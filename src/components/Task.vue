<template>
      <div>
          <div><slot>{{ index }}</slot></div>
          <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
      </div>
</template>

<script>
export default {
  props: ['task', 'index']
}
</script>

<style>
</style>
