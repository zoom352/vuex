<template>
  <div id="app">
    <PostForm/>
    <p>{{postsCount}}</p>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters} from "vuex";
import {mapActions} from 'vuex';
import PostForm from'./components/PostForm.vue'

export default {
  name: "App",
  // computed: {
  //   allPosts() {
  //     return this.$store.getters.allPosts;
  //   }
  // },
  computed: mapGetters(["allPosts", "postsCount", "validPosts"]),
  methods: mapActions(['fetchPosts']),
  components: {PostForm},
  async mounted() {
    // this.$store.dispatch('fetchPosts');
    this.fetchPosts(4);
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  width: 400px;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}

</style>
