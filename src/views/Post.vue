<template>
    <div>
      <Post v-bind:postId="postId"/>
    </div>
</template>

<script>
import Post from '@/components/Post.vue'

export default {
  name: 'post',
  components: {
    Post
  },
  data() {
    return {
      postId:this.$route.params.id
    }
  },
}
</script>
