<template>
  <div>
    <form @submit.prevent>
      <h4>Create your post</h4>
      <!-- @input="(event) => (post.title = event.target.value)" -->
      <!-- :value="post.title" -->
      <my-input
        v-model="post.title"
        type="text"
        placeholder="name"
      />
      <!-- @input="(event) => (post.body = event.target.value)"
        :value="post.body"    -->
      <my-input
        v-model="post.body"
        type="text"
        placeholder="describe"
      />
      <my-button class="btn" @click="createPost" style="align-self: flex-end; margin-top: 10px;">Add</my-button>
    </form>
  </div>
</template>

<script>
// import MyButton from '@/components/UI/MyButton';
export default {
  // components: {
  //   MyButton
  // },
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost() {
    //   const newPost = {
    //     id: Date.now(),
    //     title: this.title,
    //     body: this.body,
    //   };
    this.post.id= Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    },
  }
};
</script>

<style scoped>

form {
  display: flex;
  flex-direction: column;
}

</style>
