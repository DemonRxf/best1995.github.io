<template>
  <div id="app">
    <div class="footer">
      <span>只是单纯的收集，方便自己使用，如果感觉不错可以收藏哈，不定点更新，基本都是免费无需注册的</span>
    </div>
    <div class="con">
      <router-view/>
    </div>
    <div class="footer">
      <span>© 2020 小黑屋工具 <a href="https://beian.miit.gov.cn/#/Integrated/index">晋ICP备19004765号-1</a></span>
      <span class="explain">本站所有网页工具均从互联网精心收集，如果侵犯了您的权益，请联系我纠正或删除，E-mail:lonely3642@163.com</span>
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
    background: #000;
    text-align: center;
    padding: 20px 10px;
    display: flex;
    flex-direction: column;
    font-size: 13px;
    color: #FFf;
    a{
      color: #fff;
      &:hover{
        color: #fff;
        text-decoration:underline;
      }
    }
  }
  .explain{
    font-size: 12px;
    margin-top: 10px;
  }
</style>
