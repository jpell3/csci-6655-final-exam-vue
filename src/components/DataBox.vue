<template>
  <h3>Fetched {{numResponses}} Words</h3>
  <div v-if="numResponses" class="container">
    <DataItem :key="response" v-for="response in responses" :response="response"/>
  </div>
  <div v-if="!numResponses" class="container">
      <p><span style="font-weight: bold">No Results.</span> Please type a word and select a category above.</p>
  </div>

</template>

<script>
import DataItem from './DataItem.vue';

export default {
  name: 'DataBox',
  components: {
    DataItem,
  },
  props: {
    responses: Array,
    numResponses: Number,
  }
}
</script>

<style scoped>

.container {
  max-width: 75%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  gap: 20px;
  margin: 0 auto;
  position: relative;
}

 @media only screen and (max-width: 600px) {
    .container {
      max-width: 80%;
    }
  }

</style>