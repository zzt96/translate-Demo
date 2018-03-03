<template>
  <div>
    <form v-on:submit="formSubmit">
      <input type="text" v-model="texttoTranslate" placeholder="plz input text here">
      <select name="" id="">
        <option value="en">English</option>
        <option value="ch">Chinese</option>
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
        texttoTranslate: ""
      }
    },
    methods: {
      formSubmit: function (e) {
        // alert(this.texttoTranslate)
        this.$emit('formSubmit', this.texttoTranslate);
        e.preventDefault();
      },

    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
