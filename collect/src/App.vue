<template>
  <div id="app">
    <div class="con">
      <router-view/>
    </div>
    <div class="footer">
      <span>© 2020 晋ICP备19004765号-1</span>
      <span style="margin-left: 10px">联系QQ：384277895</span>
    </div>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.con{
  min-height: 95vh;
}
  .footer{
    text-align: center;
    padding: 10px 0 20px;
  }
</style>
