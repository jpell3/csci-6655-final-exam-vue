<template>
  <div class="container">
    <h5>Copyright © 2023</h5>
    <h5>All data is sourced from the <a href="https://www.datamuse.com/api/" target="_blank">Datamuse API</a>.</h5>
  </div>
</template>

<script>
  export default {
    name: 'AppFooter',
  }
</script>

<style scoped>
  h5:last-of-type {
    margin-top: -15px
  }

  .container {
    background-color: #FEEFDD;
    color:#3A2E39;
    border-bottom-left-radius: 50px;
    border-bottom-right-radius: 50px;
  }
</style>