<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 易用 便捷</h5>
    <translateForm v-on:formSubmit="translate"></translateForm>
    <translateOutput></translateOutput>
  </div>
</template>

<script>
  import translateForm from './components/translateForm'
  import translateOutput from './components/translateOutput'

  export default {
    name: 'App',
    components: {
      translateForm,
      translateOutput
    },
    methods: {
      translate: function (text) {
        alert(text)
      }
    }
  }
</script>

<style>
  #app {
    text-align: center;
  }
</style>
