<template>
  <div id="content">
    <div class="detail">
      <img alt="Vue logo" src="../assets/logo.png" />
      <BlogDetail />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import BlogDetail from "@/components/BlogDetail.vue";

export default {
  name: "home",
  components: {
    BlogDetail
  }
};
</script>
