<template>
    <div>
        <h1>Home Page</h1>
        <button @click="logout">Logout</button>
    </div>
</template>

<script setup lang="ts">
   const logout = () => {
  localStorage.removeItem('isAuthenticated');
  localStorage.removeItem('user');
  window.location.href = '/login';
}
</script>

<style lang="scss" scoped>

</style>