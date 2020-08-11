<template>
        <li v-for="(task, key) in tasks" :key="key">
          <div>{{ task.name }} ({{ key }})</div>
          <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
          <button @click="deleteTask(key)">xy</button>
          </li>
</template>

<script>
</script>

<style>
</style>
