<template>
  <div class="hello">
    <h1>{{ post.title.rendered }}</h1>
    <div v-html="post.content.rendered"></div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Post',
  props: {
    postId: {
      type:String,
      default:0
    }
  },
  data(){
    return {
      post:[]
    }
  },
  mounted() {
    this.getPosts();
  },
  methods:{
  	getPosts: function(){
      axios.get( 'http://rhythm-onchi.com/wp-json/wp/v2/posts/'+this.postId )
      .then( response => {
        console.log(response.data)
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
