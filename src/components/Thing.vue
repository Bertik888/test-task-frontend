<template>
  <div class="box">
    {{ name }}
  </div>
</template>

<script>
  export default {
    name: 'Thing',
    props: {
      name: {
        type: String,
        default: ''
      }
    }    
  }
</script>

<style lang="scss">
.box {
  width: 100%;
  height: 50px;
  border: solid 1px #000;
  background-color: #42b983;
  color: #000;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}
</style>