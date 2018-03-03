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
    created:function(){
      this.language ="en"
    },
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
