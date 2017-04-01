<template>
  <div id="app" class="text-center">
    <h1 >Translator</h1>
    <h5>Powered by Vue.js</h5>
    <tl_form v-on:formSubmit="translateText"></tl_form>
    <tl_output v-text="translatedText"></tl_output>
  </div>
</template>

<script>
import tl_form from "./components/tl_form"
import tl_output from "./components/tl_output"
export default {
  name: 'app',
  components: {
    tl_form,
    tl_output
  },
  data: function () {
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text, lang) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170331T233944Z.c952fd15441ca19a.c3c11a06558fda244b43dc7d4fcd5c2f6f22c9e3&lang=' + lang + '&text=' + text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      } );
    }
  }
}
</script>

<style>

</style>
