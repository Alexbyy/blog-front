<template>
  <div id="app">
    <Login v-if="showLogin" :toggleShow="toggleShow" />
    <NewAccount v-if="showNew" :toggleShow="toggleShow" />
    <div id="nav">
      <div class="nav-wrap">
        <div class="til">
          <span class="til-name">
            <router-link to="/">首页</router-link>
          </span>
          <span class="til-name">
            <router-link to="/newblog">新建</router-link>
          </span>
        </div>
        <div class="til-l">
          <div class="til-con">
            <div class="til-name-1" v-on:click="toggleShow('login')">登录</div>
            <div class="til-name" v-on:click="toggleShow('new')">注册</div>
          </div>
        </div>
      </div>
    </div>
    <div class="line-small"></div>
    <router-view />
  </div>
</template>

<script>
// @ is an alias to /src
import Login from "@/components/Login.vue";
import NewAccount from "@/components/NewAccount.vue";

export default {
  name: "App",
  data() {
    return {
      showLogin: false,
      showNew: false
    };
  },
  components: {
    Login,
    NewAccount
  },
  methods: {
    toggleShow(mode) {
      if (mode == "login") {
        this.showLogin ? (this.showLogin = false) : (this.showLogin = true);
      } else if (mode == "new") {
        this.showNew ? (this.showNew = false) : (this.showNew = true);
      }
    }
  }
};
</script>

<style lang="less">
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #f8f8f8;
}
#content {
  width: 1080px;
  background-color: #ffffff;
  margin: 0 auto;
  height: 1080px;
}
.line-small {
  width: 1080px;
  background-color: #f8f8f8;
  margin: 0 auto;
  height: 20px;
}
#nav {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 45px;
  background-color: #333333;
  margin: 0 auto;
  color: #f3f3f3;
  .nav-wrap {
    width: 1080px;
    .til{
      float: left;
      .til-name{
        margin-right:10px; 
      }
    }
    .til-l {
      float: right;
      display: flex;
      flex: 1;
      text-align: right;
      flex-direction: right;
      .til-con {
          display: flex;
          float: right;
        .til-name-1 {
          
        }
      }
    }
    .til-name {
      width: 50px;
    }
  }
  a {
    font-weight: bold;
    color: #f3f3f3;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
