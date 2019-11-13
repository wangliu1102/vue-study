<template>
  <div v-if="!repoUrl">loading</div>
  <div v-else>most star repo is <a :href="repoUrl">{{repoName}}</a></div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'App',
    data() {
      return {
        repoUrl: '',
        repoName: ''
      }
    },
    mounted() {
      //  使用vue-resource发ajax请求获取数据
      const url = `https://api.github.com/search/repositories?q=v&sort=stars`
      // this.$http.get(url).then((response) => {
      //   // success callback
      //   const result = response.data
      //   // 得到最受欢迎的repo
      //   const mostRepo = result.items[0]
      //   this.repoUrl = mostRepo.owner.html_url
      //   this.repoName = mostRepo.name
      // }, (response) => {
      //   // error callback
      //   console.log(response.statusText) // 错误信息
      //   alert('请求失败')
      // })

      // 使用axios发送ajax请求
      axios.get(url).then(response => {
        // success callback
        const result = response.data
        // 得到最受欢迎的repo
        const mostRepo = result.items[0]
        this.repoUrl = mostRepo.owner.html_url
        this.repoName = mostRepo.name
      }).catch(error => {
        console.log(error.message)
        alert('请求失败')
      })
    }
  }
</script>

<style scoped>

</style>
