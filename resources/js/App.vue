<template>
  <div >
   
      <ul >
        <li >
          <router-link to="/" >Home</router-link>
        </li>
        <li >
          <router-link to="/create" >Create Post</router-link>
        </li>
        <li >
          <router-link to="/posts" >Posts</router-link>
        </li>
      </ul>
    <br />
  
      <router-view></router-view>
   
  </div>
</template>


<script>

    export default{
    }
</script>