<template>
  <div>
      <h1>Posts</h1>
        <div>
          <div >
            <router-link :to="{ name: 'create' }">Create Post</router-link>
          </div>
        </div><br />

        <table >
            <thead>
            <tr>
                <th>ID</th>
                <th>Item Name</th>
                <th>Item Price</th>
                <th>Actions</th>
            </tr>
            </thead>
            <tbody>
                <tr v-for="post in posts" :key="post.id">
                    <td>{{ post.id }}</td>
                    <td>{{ post.title }}</td>
                    <td>{{ post.body }}</td>
                    <td><router-link :to="{name: 'edit', params: { id: post.id }}" >Edit</router-link></td>
                    <td><button  @click.prevent="deletePost(post.id)">Delete</button></td>
                </tr>
            </tbody>
        </table>
  </div>
</template>

<script>
  export default {
      data() {
        return {
          posts: []
        }
      },
      created() {
      let uri = 'http://127.0.0.1:8000/api/posts';
      this.axios.get(uri).then(response => {
        this.posts = response.data.data;
      });
    },
    methods: {
      deletePost(id)
      {
        let uri = `http://127.0.0.1:8000/api/post/delete/${id}`;
        this.axios.delete(uri).then(response => {
          this.posts.splice(this.posts.indexOf(id), 1);
        });
      }
    }
  }
</script>
