<template>
  <div class="wrap">
    <div class="con">
      <div class="blog-list-con">
        <div class="title">{{ this.blogData.title }}</div>
        <div class="author">{{ this.blogData.author }}</div>
        <div class="content">{{ this.blogData.content }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "BlogDetail",
  props: {},
  beforeMount() {
    console.log("this.router", this.$router);
    let id = this.$router.currentRoute.query.id;
    axios
      .get("/api/blog/detail", {
        params: {
          id: id
        }
      })
      .then(res => {
        this.blogData = res.data.data;
        console.log("this.blogDetailDatas", this.blogData);
      })
      .catch(err => {
        console.log("get bloglist error:", err);
      });
  },
  data() {
    return {
      blogData: [
        {
          id: 1,
          title: "标题Aadwadawdawdawdawdwadaw",
          content: "内容B",
          createtime: 1556590591933,
          author: "alex"
        },
        {
          id: 2,
          title: "标题Bwadawdawdawdawda",
          content: "内容B",
          createtime: 1556590591933,
          author: "lisi"
        }
      ],
      blogDatas: []
    };
  },
  methods: {
    goDetail(blogID) {
      this.$router.push({ path: "/detail", query: { id: blogID } });
    },
    timestampToTime(timestamp) {
      var date = new Date(timestamp); //时间戳为10位需*1000，时间戳为13位的话不需乘1000
      var Y = date.getFullYear() + "-";
      var M =
        (date.getMonth() + 1 < 10
          ? "0" + (date.getMonth() + 1)
          : date.getMonth() + 1) + "-";
      var D = date.getDate() + " ";
      var h = date.getHours() + ":";
      var m = date.getMinutes() + ":";
      var s = date.getSeconds();
      return Y + M + D + h + m + s;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.wrap {
  margin: 0 auto;
}
.line-big {
  width: 1080px;
  border: 1px solid #e7e7e7;
}
.line {
  border: 0.5px solid #e7e7e7;
}
.blog-list-con {
  .til-wrap {
    padding: 0 20px;
    height: 40px;
    margin-top: 10px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
  }
  .til-con {
    display: flex;
    justify-content: flex-start;
    .title {
      text-align: left;
      flex: 1;
      cursor: pointer;
      font-family: "Helvetica Neue", Helvetica, Arial, "Microsoft Yahei",
        "Hiragino Sans GB", "Heiti SC", "WenQuanYi Micro Hei", sans-serif;
    }
    .time {
      flex-basis: 275px;
    }
    .author {
      flex-basis: 70px;
    }
  }
}
</style>
