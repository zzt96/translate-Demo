<template>
  <div>
    <h2>{{translatedText}}</h2>
  </div>
</template>

<script>
  export default {
    name: 'translateOutput',
    /**
     * 父组件给子组件传值：子组件使用props接收
     */
    props: [
      "translatedText"
    ]
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
