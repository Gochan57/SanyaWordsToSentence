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
    onNewSentence: function (sentence) {
      this.words = this.splitSentenceToWords(sentence)
      this.selectedWordIds = []
      this.unselectedWordIds = this.words.map(word => word.id)
    },
    splitSentenceToWords: function (sentence) {
      // TODO split this.sentence to words with ids
      return sentence.trim().split(" ").map((word, i) => {
        return {
          value: word,
          id: i
        }
      })
      // return [
      //   {value: 'Hello', id: 1},
      //   {value: 'mr', id: 2},
      //   {value: 'Sanya', id: 3},
      // ]
    },
    onWordSelect: function (wordId) {
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
      if (this.unselectedWordIds.length) return false
      // TODO check if this.selectedWords together is the same as this.sentence
      return true
    }
  },
  watch: {
    sentence(newSentence, oldSentence) {
      this.onNewSentence(newSentence)
    }
  },
  mounted() {
    this.onNewSentence(this.sentence)
  }
}
</script>

<template>
  <div>
    <SentenceAssembler class="block" :words="selectedWords" @tapped="onWordUnselect"/>
    <WordsSelector class="block" :words="unselectedWords" @tapped="onWordSelect"/>
  </div>
</template>

<style scoped>
</style>
