<template>
  <AppHeader />
  <AppBody :responses="responses" :numResponses="numResponses" @generateList='generateNew'/>
  <AppFooter />
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppBody from './components/AppBody.vue';
import AppFooter from './components/AppFooter.vue';

  export default {
    name: 'App',
    components: {
      AppHeader,
      AppBody,
      AppFooter,
    },
    data() {
      return {
        responses: [],
        numResponses: 0,
        inputWord: '',
        inputCode: '',
        updateKey: false,
        apiURL: 'https://csci-6655-final-exam-server.onrender.com/api',
      }
    },
    methods: {
      async fetchData(apiURL) {
        const res = await fetch(apiURL);
        const data = await res.json();
        return data;
      },
      async generateNew(inputCode, inputWord) {
        if(!inputCode || !inputWord) {
          alert('You must enter a word and select a category before fetching a new list.');
        } else {
          this.inputCode = inputCode;
          this.inputWord = inputWord;
          this.apiURL = `https://api.datamuse.com/words?rel_${inputCode}=${inputWord}`;
          this.responses = await this.fetchData(this.apiURL);
          this.numResponses = this.responses.length;
          console.log(`LOG: inputWord=${inputWord}  inputCode=${inputCode}  apiURL=${this.apiURL}`);
        }
      },
    },
    async mounted() {
      this.responses = await this.fetchData(this.apiURL);
      this.numResponses = this.responses.length;
    },
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #3A2E39;
    margin-top: 45px;
    height: 90vh;
  }

  body {
    background-color: #9d8189bb;
  }

  .container {
    width: 90%;
    margin: 10px auto;
    padding: 10px 0;
  }

  @media only screen and (max-width: 600px) {
    #app {
      margin: 0;
    }
  }
</style>