<template>
  <div>
    <h1>Create A Post</h1>
    <form @submit.prevent="addPost">
     <div>
            <label>Post Title:</label>
            <input type="text"  v-model="post.title">
     </div>
        <div>
         
              <label>Post Body:</label>
              <textarea  v-model="post.body" row="5" ></textarea>
         
        </div>
        <br />
        <div >
          <button >Create</button>
        </div>
    </form>
  </div>
</template>

<script>
    export default {
        data(){
        return {
          post:{}
        }
    },
    methods: {
  addPost(){
    let uri = 'http://127.0.0.1:8000/api/post/create';
    this.axios.post(uri, this.post).then((response) => {
       this.$router.push({name: 'posts'});
    });
}
    }
  }
</script>