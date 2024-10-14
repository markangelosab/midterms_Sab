<template>
  <div>
    <h2>Welcome to the Product Management App</h2>
    <p>Name: Mark Angelo Sab</p>
    <p>Program: BSIT-3</p>
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/products">Products</router-link>
    </nav>
    <img src="@/assets/background.jpg" alt="Background" />
  </div>
</template>

<script>
export default {
  name: 'Home'
};
</script>

<style scoped>
/* Add some styling for the home page */
</style>
