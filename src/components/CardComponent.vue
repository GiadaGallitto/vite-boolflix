    <script>
    export default {
      props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: String,
      }
    }
    </script>

<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <h5>{{ originalTitle }}</h5>
    <p>{{ language }}</p>
    <span>{{ vote }}</span>
  </div>
</template>

<style lang="scss">
  
</style>