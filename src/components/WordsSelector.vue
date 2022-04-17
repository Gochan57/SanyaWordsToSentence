<script>
import Word from "./Word.vue";

export default {
  components: {Word},
  props: ['words'],
  methods: {
    onWordTapped: function (wordId) {
      this.$emit('tapped', wordId)
    }
  }
}
</script>

<template>
  <div class="words-container">
    <div class="word-wrapper" v-for="word in words">
      <Word :word="word" @tapped="onWordTapped"/>
    </div>
  </div>
</template>

<style scoped>
.words-container {
  display: flex;
  margin-top: 10px;
}
.word-wrapper {
  padding-right: 5px;
}
</style>
