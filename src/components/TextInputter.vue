<script>
export default {
  methods: {
    onTextChanged: function (e) {
      this.text = e.target.value
    },
    onSubmitButtonClicked: function () {
      this.$emit("submitted", this.text)
    }
  }
}
</script>

<template>
  <div class="container">
    <div>
        Put your text here and submit
    </div>
    <div>
      <textarea class="wide-textarea" rows="3" @change="onTextChanged">{{text}}</textarea>
    </div>
    <div>
      <button @click="onSubmitButtonClicked">Submit</button>
    </div>
  </div>
</template>

<style scoped>
container {

}

h3 {
  font-size: 1.2rem;
}

.wide-textarea {
  width: 100%;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -ms-box-sizing: border-box;
  box-sizing: border-box;
}

</style>
