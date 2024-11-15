<script>
export default {
  data () {
    return {
      name: 'Tazwar Saif',
      status: 'pending',
      tasks : ['task1','task2','task3'],
      link: 'https://google.com'
    }
  },
  methods: {
    toggleStatus () {
      this.status = !this.status
    }
  }
}

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status==='active'">User is active</p>
  <p v-else-if="status==='pending'">Pending</p>
  <p v-else>Inactive</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks">{{ task }}</li>
  </ul>
  <a :href="link">google</a>

  <button v-on:click="toggleStatus">Change Status</button>
  <button @click="toggleStatus">Change Status</button>
</template>
