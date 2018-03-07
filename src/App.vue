<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单 易用 便捷</h5>
    <translateForm v-on:formSubmit="translate"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
  /**
   * 主组件引用子组件
   * translateForm：包括一个表单，包含待翻译内容和翻译语言选项
   * translateOutput：翻译显示区域
   */
  import translateForm from './components/translateForm'
  import translateOutput from './components/translateOutput'

  export default {
    name: 'App',//组件名称
    /**
     * 组件所需数据注册
     */
    data(){
      return{
        translatedText:""
      }
    },
    /**
     * 组件注册
     */
    components: {
      translateForm,
      translateOutput
    },
    /**
     * 方法
     *
     */
    methods: {
      /**
       * translate函数：子组件给父组件传值：通过事件
       * 子组件点击翻译按钮后：触发formSubmit事件，向本父组件传递this.texttoTranslate,this.language
       * 这个方法使用两个参数接收
       * @param text 接收待翻译文本
       * @param language 接收指定语言选项
       * get方法请求api
       * 根据yandex的要求拼接：api网址？key&lang&text
       * 返回response：response.body.text[0]即是翻译之后的文本
       * 将这个值赋给translatedText，子组件translateOutput使用props接收
       */
      translate: function (text,language)  {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180303T030148Z.6d04e84d3ccda8f3.422f83d240333dbf4052683778b554049ec98e18&lang='+language+'&text='+text)
        .then((response)=>{
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
