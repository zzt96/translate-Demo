<template>
  <div>
    <form v-on:submit="formSubmit">
      <input type="text" v-model="texttoTranslate" placeholder="plz input text here">
      <select v-model="language">
        <option value="en">English</option>
        <option value="it">Italian</option>
        <option value="ko">Korean</option>
        <option value="es">spanish</option>
      </select>
      <input type="submit" value="translate">
    </form>
  </div>
</template>

<script>
  export default {
    name: 'translateForm',

    data() {
      return {
        texttoTranslate: "",
        language:""
      }
    },
    /**
     * 默认给选择语言一个英语
     */
    created:function(){
      this.language ="en"
    },
    /**
     * formSubmit表单提交绑定的方法，在上面使用v-model双向绑定
     */
    methods: {
      formSubmit: function (e) {
        this.$emit('formSubmit', this.texttoTranslate,this.language);
        e.preventDefault();
      },

    }
  }
</script>

<style scoped>

</style>
