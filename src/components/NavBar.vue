<template>
  <nav class="main-nav">
      <router-link to="/">Projects</router-link>
      <router-link :to="{name: 'AddProject'}">Add Project</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style scoped>
    .main-nav {
        text-align: center;
        margin: 40px auto;
    }
    .main-nav a {
        display: inline-block;
        margin: 0 10px;
        text-decoration: none;
        font-size: 20px;
        color: darkslategray;
    }
    a.router-link-active {
        border-bottom: 2px solid rgb(6, 158, 158);
        padding-bottom: 5px;
        color: lightseagreen;
    } 
</style>