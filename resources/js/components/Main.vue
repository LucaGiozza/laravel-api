<template>
 <div class="container">
        <div class="row">
  <div class="col-sm-6" v-for="post in posts" :key="post.id">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title"></h5>
        <p class="card-text">{{post.content}}.</p>
        <a href="#" class="btn btn-primary">altro</a>
      </div>
    </div>
  </div>
  <div class="col-sm-6">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">Special title treatment</h5>
        <p class="card-text">With supporting text below as a natural lead-in to additional content.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>
</div>
 </div>
</template>

<script>
export default {
    name: "Main",
    data(){
        return{
            callApi: 'http://localhost:8000/api/posts',
            posts:[]
        }
    },

    created(){
        this.getPosts();
        

    },

    methods:{
        getPosts(){
            axios.get(this.callApi)
                 .then(response => {
                     console.log(this.posts);
                     this.posts = response.data.results;
                 })
                 .catch();
        }
    
    }

}
</script>

<style lang="scss" scoped>

</style>