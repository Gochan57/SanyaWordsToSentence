<script>
import SentenceAssembler from "./SentenceAssembler.vue";
import WordsSelector from "./WordsSelector.vue";

export default {
  components: {WordsSelector, SentenceAssembler},
  props: ['sentence'],
  data() {
    return {
      words: [],
      selectedWordIds: [],
      unselectedWordIds: []
    }
  },
  computed: {
    selectedWords: function () {
      return this.selectedWordIds.map(wordId => this.words.find(word => word.id === wordId))
    },
    unselectedWords: function () {
      return this.unselectedWordIds.map(wordId => this.words.find(word => word.id === wordId))
    },
  },
  methods: {
    splitSentenceToWords: function (sentence) {
      // TODO split this.sentence to words with ids
      return [
        {value: 'Hello', id: 1},
        {value: 'mr', id: 2},
        {value: 'Sanya', id: 3},
      ]
    },
    onWordSelect: function (wordId) {
      console.log(`onWordSelect(${wordId})`)
      this.selectedWordIds.push(wordId)
      const indexToRemove = this.unselectedWordIds.indexOf(wordId)
      this.unselectedWordIds.splice(indexToRemove, 1)
    },
    onWordUnselect: function (wordId) {
      const indexToRemove = this.selectedWordIds.indexOf(wordId)
      this.selectedWordIds.splice(indexToRemove, 1)
      this.unselectedWordIds.push(wordId)
    },
    check: function () {
      console.log(`check "${this.sentence}"`)
      if (this.unselectedWordIds.length) return false
      // TODO check if this.selectedWords together is the same as this.sentence
      return true
    }
  },
  mounted() {
    this.words = this.splitSentenceToWords(this.sentence)
    this.unselectedWordIds = this.words.map(word => word.id)
  },
}
</script>

<template>
  <div class="container">
    <SentenceAssembler :words="selectedWords" @tapped="onWordUnselect"/>
    <WordsSelector :words="unselectedWords" @tapped="onWordSelect"/>
  </div>
</template>

<style scoped>
.container {
  margin-top: 20px;
}
</style>
