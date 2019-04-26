<template>
<div calss="pages">
  <ul v-for="post in posts">
    <li>
      <router-link v-bind:to="{ name:'post', params:{ id:post.id } }">{{post.title.rendered}}</router-link>
    </li>
  </ul>
</div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
import VueAxios from 'vue-axios'

export default {
  name: 'pages',
  components: {},
  data() {
    return {
      posts: []
    }
  },
  mounted() {
    this.getPosts();
  },
  methods:{
  	getPosts: function(){
      axios.get( 'http://rhythm-onchi.com/wp-json/wp/v2/posts/' )
      .then( response => {
        console.log(response.data);
        this.posts = response.data;
      } )
      .catch( error => {
        window.alert( error );
      } );
    }
  }
}
</script>
