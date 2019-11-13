<template>
  <mt-button @click="handleClick" type="primary" style="width: 100%">Test</mt-button>
</template>

<script>
  import {Toast} from 'mint-ui'

  export default {
    name: 'App',
    methods: {
      handleClick() {
        Toast(' 点击了测试');
      }
    }
  }
</script>

<style scoped>

</style>
