<template>
  <div class="wrap">
    <div class="con">
      <div class="ipt">
        <input v-model="username" placeholder="请输入用户名" />
      </div>
      <div class="ipt">
        <input v-model="password" placeholder="请输入密码" />
      </div>
      <div class="btn-con">
        <button v-on:click="login">确定</button>
        <button v-on:click="close">取消</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "BlogList",
  props: ["toggleShow"],
  data() {
    return {
      username: "",
      password: ""
    };
  },
  methods: {
    close() {
      this.toggleShow("login");
    },
    login() {
      const instance = axios.create({
        baseURL: "http://47.106.34.113",
        timeout: 2500
      });
      instance.defaults.headers.common["Content-Type"] = "application/json";
      let postData = {
        username: this.username,
        password: this.password
      };
      const options = {
        method: "POST",
        headers: { "content-type": "application/json" },
        data: postData,
        url: "/api/user/login"
      };
      axios(options)
        .then(response => {
          console.log(response);
          alert("登陆成功");
          this.close();
        })
        .catch(function(error) {
          console.log(error);
          alert("登录失败请重试");
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.wrap {
  z-index: 200;
  width: 100%;
  min-height: 1500px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: absolute;
  background-color: #f0f0f0;
  opacity: 0.8;
  .con {
    position: absolute;
    left: 50%;
    top: 200px;
    width: 30%;
    height: 300px;
    margin-left: -15%;
    border: 1px solid #333333;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: #ffffff;
    .btn-con {
      display: flex;
      justify-content: center;
      align-items: center;
      button {
        margin-right: 10px;
      }
    }
    .ipt {
      width: 80%;
      padding: 18px 0;
      input {
        width: 80%;
        height: 30px;
      }
    }
  }
}
</style>
