<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 易用 便捷</h5>
    <translateForm v-on:formSubmit="translate"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
  import translateForm from './components/translateForm'
  import translateOutput from './components/translateOutput'

  export default {
    name: 'App',
    data(){
      return{
        translatedText:""
      }
    },
    components: {
      translateForm,
      translateOutput
    },
    methods: {
      translate: function (text,language)  {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180303T030148Z.6d04e84d3ccda8f3.422f83d240333dbf4052683778b554049ec98e18&lang='+language+'&text='+text)
        .then((response)=>{
          // console.log(response.body.text[0]);
          this.translatedText = response.body.text[0];//少this读不到translatedText
        })

      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
