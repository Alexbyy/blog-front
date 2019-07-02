<template>
  <div id="content">
    <div class="home">
      <img alt="Vue logo" src="../assets/logo.png" />
      <BlogList />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import BlogList from "@/components/BlogList.vue";

export default {
  name: "home",
  components: {
    BlogList
  }
};
</script>
