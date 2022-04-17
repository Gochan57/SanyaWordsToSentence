<script>
import SentenceArea from "./SentenceArea.vue";

export default {
  components: {SentenceArea},
  props: ['text'],
  data() {
    return {
      sentences: [],
      checked: false,
      success: false
    }
  },
  methods: {
    onNewText: function (text) {
      this.sentences = this.splitTextToSentences(text)
    },
    splitTextToSentences: function (text) {
      // TODO split text to sentences
      return [
        'The first sentence',
        'The second sentence',
      ]
    },
    check: function () {
      let res = true
      for (let i = 0; i < this.$refs.sentences.length; i++) {
        if (!this.$refs.sentences[i].check()) res = false
      }
      this.checked = true
      this.success = res
    }
  },
  watch: {
    text(newText, oldText) {
      this.onNewText(newText)
    }
  },
  mounted() {
    this.onNewText(this.text)
  }
}
</script>

<template>
  <div class="container">
    <SentenceArea v-for="(sentence) in sentences" :sentence="sentence" ref="sentences"/>
    <div class="check-container">
      <button class="button-check" @click="check">Check</button>
      <span v-if="checked && success">Right!</span>
      <span v-if="checked && !success">Wrong!</span>
    </div>
  </div>
</template>

<style scoped>
.check-container {
  margin-top: 30px;
}
.button-check {
  margin-right: 10px;
}
</style>
