<template>
  <main>
    <h1 class="title">SSR Example</h1>
    <nuxt-link to="/nyc" title="New York">New York</nuxt-link>
  </main>
</template>

<script>
export default {};
</script>

<style>
main {
  margin: 0 auto;
  width: 800px;
}
.title {
  text-align: center;
}
</style>
