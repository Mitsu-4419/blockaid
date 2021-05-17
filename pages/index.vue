<template>
  <section class="index">
    <Navigation></Navigation>
    <card 
        v-for="(post, i) in posts" 
        :key="i"
        :title="post.fields.title"
        :id="post.sys.id"
        :date="post.sys.updatedAt" 
    />
  </section>
</template>

<script>
import Card from "~/components/card.vue";
import Navigation from "~/components/Navigation.vue";
import {createClient} from "~/plugins/contentful.js"

const client = createClient()
export default {
  transition:'slide-left',
  components:{
    Card
  },
  asyncData({env, params}){
    return client
    .getEntries(env.CTF_BLOG_POST_TYPE_ID)
    .then(entries =>{
      return {
        posts:entries.items
      }
    })
    .catch(console.error)
  }
}
</script>

<style>

</style>
