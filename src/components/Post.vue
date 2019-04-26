<template>
  <div class="hello">
    <h1>{{ post.title.rendered }}</h1>
    <div v-html="post.content['rendered']"></div>
  </div>
</template>

<script>
import axios from 'axios'
import constant from '@/definition/constant.js';
export default {
  name: 'Post',
  props: {
    postId: {
      type:String,
      default:"0"
    }
  },
  data(){
    return {
      post:[],
      wpJsonLink:constant.SITE_URL + constant.REST_API + this.postId
    }
  },
  mounted() {
    this.getPosts();
  },
  methods:{
  	getPosts: function(){
      axios.get( this.wpJsonLink )
      .then( response => {
        this.post = response.data;
      } )
      .catch( error => {
        window.alert( error );
      } );
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
