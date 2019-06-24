<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">首页</router-link>|
      <router-link to="/about">关于</router-link>
    </div>
    <div class="line-small"></div>
    <router-view/>
  </div>
</template>

<style lang="less">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #F8F8F8;
}
#content {
  width: 1080px;
  background-color: #ffffff;
  margin: 0 auto;
  height: 1080px;
}
.line-small{
  width: 1080px;
  background-color: #F8F8F8;
  margin: 0 auto;
  height: 20px;
}
#nav {
  width: 1080px;
  height: 45px;
  background-color: #ffffff;
  margin: 0 auto;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
