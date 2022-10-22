<template>
<Card/>
</template>

<script>
import Card from '@/components/Card.vue'
export default {
  name: 'App',
  components: {
    Card
  }
}
</script>

<style lang="scss">
*{
  padding: 0;
  margin:0;
}
#app {
  font-family: 'Houschka Pro';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}
</style>
