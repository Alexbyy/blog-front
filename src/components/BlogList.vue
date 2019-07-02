<template>
  <div class="wrap">
    <div class="con">
      <div class="blog-list-con">
        <div class="line-big"></div>
        <div class="til-wrap" v-for="item in blogData" :key="item.id">
          <div class="til-con">
            <span class="title">{{ item.title }}</span>
            <span class="time">{{ item.createtime }}</span>
            <span class="author">{{ item.author }}</span>
          </div>
          <div class="line"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BlogList",
  props: {},
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
      ]
    };
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
      font-family: "Helvetica Neue", Helvetica, Arial, "Microsoft Yahei",
        "Hiragino Sans GB", "Heiti SC", "WenQuanYi Micro Hei", sans-serif;
    }
    .time {
      flex-basis: 30px;
    }
    .author {
      flex-basis: 30px;
    }
  }
}
</style>
