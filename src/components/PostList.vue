<template>
  <div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8">
    <ul class="my-10">
      <li
        v-for="(post, i) in posts"
        :key="post.id"
        :class="[
          'tab-pane fade',
          i === 0
            ? 'md:w-full mx-0 relative mb-10'
            : 'md:w-1/4 mx-0 flex-col w-full h-auto md:pr-6 last:pr-0',
        ]"
      >
        <img
          :src="i === 0 ? post.image.original : post.image.large"
          :class="i === 0 ? 'h-auto' : 'h-auto aspect-auto'"
        />
        <div class="flex justify-between py-2">
          <span
            :class="
              i === 0
                ? 'absolute bottom-10 md:bottom-16 left-0 md:left-6 text-white font-bold px-4 py-2'
                : 'flex capitalize text-sm'
            "
            >{{ post.date }}</span
          >
          <span
            :class="
              i === 0
                ? 'absolute md:top-10 top-4 right-4 md:right-14 text-white bg-slate-500 px-4 py-2'
                : 'flex capitalize text-sm text-slate-400'
            "
            >{{ post.type }}</span
          >
        </div>

        <span
          :class="
            i === 0
              ? 'absolute -bottom-6 h-1 bg-slate-800 border-2 w-full'
              : 'hidden h-0'
          "
          >&nbsp;</span
        >
        <!-- <img :src="post.image /> -->
        <div
          :class="[
            'flex flex-col font-bold',
            i === 0
              ? 'md:w-full absolute bottom-0 p-4 md:p-10 bg-gradient-to-b from-transparent to-slate-900 text-2xl text-white text-left z-10'
              : 'text-left uppercase',
          ]"
        >
          <p :class="i === 0 ? '' : 'mb-10'">{{ post.title }}</p>
        </div>
        <div :class="i === 0 ? 'hidden' : 'font-bold text-right'">
          <a href="#" :title="`Read more about ${post.title}`">
            Read More &#8250;
          </a>
        </div>
      </li>
    </ul>
    <button
      @click.prevent="getMorePosts"
      class="btn py-2 px-8 mb-10 text-white"
    >
      Load More
    </button>
  </div>
</template>

<script>
import axios from "axios";
const url = `https://www.lionsrugby.com/wp-json/sotic-app-feeds/posts/?post_type=post,video`;

export default {
  name: "PostList",
  data() {
    return {
      posts: [],
      posts_per_page: 5,
      offset: 0,
    };
  },
  mounted() {
    this.getPosts();
  },
  methods: {
    toggleNav() {
      this.showMenu = !this.showMenu;
    },
    async getPosts() {
      try {
        await axios
          .get(
            url + `&posts_per_page=${this.posts_per_page}&offset=${this.offset}`
          )
          .then((res) => {
            this.posts = res.data.data;
          });
      } catch (error) {
        console.log(error);
      }
    },
    async getMorePosts() {
      try {
        this.offset = this.offset + this.posts_per_page;
        await axios
          .get(
            url + `&posts_per_page=${this.posts_per_page}&offset=${this.offset}`
          )
          .then((res) => {
            this.posts = res.data.data;
          });
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-flex;
}
.btn {
  background-color: #284b63;
}
</style>
