<template>
  <div class="app">
    <div>
      <h1>Hello VUE JS</h1>
      <div>Like {{ like }}</div>
      <div>Dislike {{ dislike }}</div>
      <button v-on:click="addLike">Like</button>
      <button @:click="adddisLike">Dislike</button>
    </div>

    <div>
      <div><strong>Name:</strong>Post about...</div>
      <div><strong>Post:</strong>Text...</div>
    </div>

    <h2>Page with posts</h2>
    <my-button @:click="showDialog">Create post</my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost"></post-form>
    </my-dialog>

    <post-list :posts="posts" @remove="removePost"></post-list>
  </div>
</template>

<script>
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      like: 0,
      dislike: 0,
      posts: [
        { id: 1, title: "Title", body: "Your post 1" },
        { id: 2, title: "Title", body: "Your post 2" },
        { id: 3, title: "Title", body: "Your post 3" },
      ],
      dialogVisible: false,
      // title: "",
      // body: "",
    };
  },
  methods: {
    addLike() {
      this.like += 1;
    },
    adddisLike() {
      this.dislike += 1;
    },
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    }
    // inputTitle () {
    //     this.title = event.target.value;
    // },
    // inputBody () {
    //     this.body = event.target.value;
    // }
  },
};
</script>

<style>
.app {
  padding: 20px;
  width: 85%;
  margin: auto;
}
</style>
