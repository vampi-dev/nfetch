pages<script setup>
const { data: users, pending, error, refresh } = await useFetch(
  'https://jsonplaceholder.typicode.com/users'
)
</script>

<template>
  <div>
    <h1>Users List</h1>

    <p v-if="pending">Loading users...</p>

    <p v-else-if="error">
      Failed to load users.
    </p>

    <div v-else>
      <div v-for="user in users" :key="user.id">
        <h3>{{ user.name }}</h3>
        <p>Email: {{ user.email }}</p>
        <p>City: {{ user.address.city }}</p>
        <hr />
      </div>

      <button @click="refresh()">Reload Users</button>
    </div>
  </div>
</template>
