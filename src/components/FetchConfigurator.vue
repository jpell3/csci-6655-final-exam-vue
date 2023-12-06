/*
-- API LINKS --
https://www.datamuse.com/api/
https://api.datamuse.com/words?rel_[CODE]=[WORD]

-- CATEGORY DESCRIPTIONS --
[code]	Description	                                                             Example
jja - Popular nouns modified by the given adjective, per Google Books Ngrams	gradual → increase
jjb - Popular adjectives used to modify the given noun, per Google Books Ngrams	beach → sandy
syn	- Synonyms (words contained within the same WordNet synset)	ocean → sea
trg	- "Triggers" (words that are statistically associated with the query word in the same piece of text.)	cow → milking
ant	- Antonyms (per WordNet)	late → early
spc	- "Kind of" (direct hypernyms, per WordNet)	gondola → boat
gen	- "More general than" (direct hyponyms, per WordNet)	boat → gondola
com	- "Comprises" (direct holonyms, per WordNet)	car → accelerator
par	- "Part of" (direct meronyms, per WordNet)	trunk → tree
bga	- Frequent followers (w' such that P(w'|w) ≥ 0.001, per Google Books Ngrams)	wreak → havoc
bgb	- Frequent predecessors (w' such that P(w|w') ≥ 0.001, per Google Books Ngrams)	havoc → wreak
hom	- Homophones (sound-alike words)	course → coarse
cns	- Consonant match	sample → simple
*/

<template>
  <h3>Fetch Configurator</h3>
  <div class="flex">
    <input type="text" v-model="inputWord" placeholder="Type a word here...">
    <select v-model="inputCode" id="inputCode">
      <option value="">(select a category)</option>
      <option value="jja">Popular Nouns</option>
      <option value="jjb">Popular Adjectives</option>
      <option value="syn">Synonyms</option>
      <option value="trg">"Triggers"</option>
      <option value="ant">Antonyms</option>
      <option value="spc">"Kind of"</option>
      <option value="gen">"More general than"</option>
      <option value="com">"Comprises"</option>
      <option value="par">"Part of"</option>
      <option value="bga">Frequent Followers</option>
      <option value="bgb">Frequent Predecessors</option>
      <option value="hom">Homophones</option>
      <option value="cns">Consonant Match</option>
    </select>
    <button @click="$emit('generateList', inputCode, inputWord)">Generate</button>
  </div>
</template>

<script>
  export default {
    name: 'FetchConfigurator',
    emits: ['generateList'],
    data() {
      return {
        inputCode: '',
        inputWord: '',
      }
    },
  }
</script>

<style>
  select, input, button {
    height: 50px;
    border: none;
    padding: 0 20px;
    cursor: pointer;
  }

  input {
    border-top-left-radius: 20px;
    border-bottom-left-radius: 20px;
  }

  button {
    border-top-right-radius: 20px;
    border-bottom-right-radius: 20px;
    background-color: lightgray;
  }

  .flex {
    display: flex;
    justify-content: center;
  }

  input {
    width: 30%;
    cursor:text;
  }

  input:focus {
    outline: none;
  }

  input:active {
    border: none;
  }

  select {
    width: 20%;
    min-width: 200px;
  }

  @media only screen and (max-width: 600px) {
    .flex {
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }

    select, button, input {
      width: 160px;
      border-radius: 20px;
      color: #3A2E39;
    }
  }
</style>