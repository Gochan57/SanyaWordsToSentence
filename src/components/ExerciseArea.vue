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
      return text.split('.')
      // return [
      //   'The first sentence',
      //   'The second sentence',
      // ]
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
  <div class="section">
    <SentenceArea class="block" v-for="(sentence) in sentences" :sentence="sentence" ref="sentences"/>
    <div class="block">
      <button class="button check-button is-primary" @click="check">Check</button>
      <span class="tag is-large is-success" v-if="checked && success">Right!</span>
      <span class="tag is-large is-danger" v-if="checked && !success">Wrong!</span>
    </div>
  </div>
</template>

<style scoped>
.check-button {
  margin-right: 10px;
}
</style>
