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
import constant from '@/definition/constant.js';

export default {
  name: 'pages',
  components: {},
  data() {
    return {
      posts: [],
      wpJsonLink:constant.SITE_URL + constant.REST_API
    }
  },
  mounted() {
    this.getPosts();
  },
  methods:{
  	getPosts: function(){
      axios.get( this.wpJsonLink )
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
