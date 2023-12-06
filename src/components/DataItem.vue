<template>
  <div class="item-container">
    <h4>{{ response.word }}</h4>
    <p>{{ response.score }}</p>
  </div>
</template>

<script>
  export default {
    name: 'DataItem',
    props: {
      response: Object,
    }
  }
</script>

<style scoped>
  .item-container {
    width: 125px;
    height: 75px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    background-color: #8b9b9c;
    border-radius: 15px;
    box-shadow: 5px 10px 5px rgba(0,0,0,0.3);
  }

  h4, p {
    margin: 0;
    padding: 5px;
  }

  p {
    font-style: italic;
  }
</style>