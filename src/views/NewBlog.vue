<template>
  <div class="content">
    <div class="til">
      <input v-model="title" placeholder="请输入文章标题" />
    </div>
    <div class="con">
      <textarea v-model="content" placeholder="请输入文章内容"></textarea>
    </div>
    <div class="btn"><button v-on:click="onSubmit()">提交</button></div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "newBlog",
  data() {
    return {
      title: "",
      content: ""
    };
  },
  methods: {
    onSubmit() {
      let data = {
        title: this.title,
        content: this.content,
        author: "byy"
      };
      axios
        .post("/api/blog/new", data)
        .then(function(response) {
          console.log(response);
          if (response.data.errno == -1) {
            alert(response.data.message);
          }
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
};
</script>
<style lang="less" scoped>
.content {
  height: 1200px;
  .btn {
    button {
      width: 70px;
      height: 30px;
    }
  }
}
.til {
  padding: 10px 0;
  input {
    width: 800px;
    height: 35px;
  }
}
.con {
  textarea {
    width: 800px;
    height: 600px;
  }
}
</style>
