<template>
    <div>
      <Post v-bind:postId="postId"/>
    </div>
</template>

<script>
import Post from '@/components/Post.vue'

export default {
  name: 'post',
  // props:{post},
  components: {
    Post
  },
  data() {
    return {
      postId:this.$route.params.id
    }
  },
  mounted() {
console.log(`hoge>>>`,this.$route.params.id)
  },
  methods:{
  }
}
</script>
