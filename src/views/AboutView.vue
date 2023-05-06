<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>{{ data }}</p>
  </div>
</template>

<script>
  export default{
    data() {
      return {
        data: {},
      }
    },
    mounted(){
      // 開發中環境變數 ↓
      console.log(import.meta.env.VITE_TEXT);
      // 通用環境變數 ↓
      // url變數 賦值import....
      const url = import.meta.env.VITE_PATH;
      // 再把radomuser網址換成 url變數
      this.$http.get(url)
        .then((response) => {console.log(response);
        this.data = response.data.results[0];
        console.log(this.data);
      });


    }
  }

</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
