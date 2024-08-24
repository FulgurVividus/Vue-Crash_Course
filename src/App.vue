<script>
export default {
  data() {
    return {
      name: "John Doe",
      status: "active",
    };
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else="status">User is not active</p>
</template>
