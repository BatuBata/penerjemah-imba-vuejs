<template>
  <div class="text-center" id="app"> 
    <h1>PENERJEMAH</h1>
    <h5 class="text-muted" >Powered By Vue.js</h5>
    <hr>
    <TranslateForm v-on:formSubmit="translateText" ></TranslateForm>
    <TranslateOutput v-text="translatedText" ></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput';

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text, languange){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170826T191816Z.10e79107fad35f20.18ea88ba5afffb2f950c143988aa7337fc5a5667&lang='+languange+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>

<style>
body {
      background: #fefefe;
}
</style>
