<template>
  <div class="home">
    <nav-header />
    <post-list />
    <footer-info />
  </div>
</template>

<script>
import NavHeader from "@/components/NavHeader.vue";
import PostList from "@/components/PostList.vue";
import FooterInfo from "@/components/FooterInfo.vue";

export default {
  name: "HomeView",
  components: {
    NavHeader,
    PostList,
    FooterInfo,
  },
};
</script>
