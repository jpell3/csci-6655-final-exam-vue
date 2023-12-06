<template>
  <div class="container">
    <FetchConfigurator @generateList='generateNew'/>
    <DataBox :responses="responses" :numResponses="numResponses" />  
  </div>
</template>

<script>
  import FetchConfigurator from './FetchConfigurator.vue'
  import DataBox from './DataBox.vue'

  export default {
    name: 'AppBody',
    components: {
      FetchConfigurator,
      DataBox,
    },
    props: {
      responses: Array,
      numResponses: Number,
    },
    emits: ['generateList'],
    methods: {
      generateNew (inputCode, inputWord) {
        this.$emit('generateList', inputCode, inputWord);
      },
    },
  }
</script>

<style>

.container {
    background-color: #FEEFDD;
    color: #3A2E39;
  }

</style>