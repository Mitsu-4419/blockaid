<template>
    <section class='blog h-screen bg-gray-200 pt-100px flex justify-center grid grid-cols-7'>
        <section class='col-span-5 bg-red-200 p-10 flex flex-wrap'>
            <!-- <card 
                v-for="(post, i) in posts" 
                :key="i"
                :title="post.fields.title"
                :id="post.sys.id"
                :content="post.sys.updatedAt" 
    
            />
            <card 
                v-for="(post, i) in posts" 
                :key="i"
                :title="post.fields.title"
                :id="post.sys.id"
                :content="post.sys.updatedAt" 
            />
            <card 
                v-for="(post, i) in posts" 
                :key="i"
                :title="post.fields.title"
                :id="post.sys.id"
                :content="post.sys.updatedAt" 
            /> -->
        </section>
        <section class='col-span-2 bg-green-200 p-10'>
            gid
        </section>
    </section>
</template>

<script>
import Thumbnail from '~/components/blog/Thumbnail.vue'
import {createClient} from "~/plugins/contentful.js"

const client = createClient()
export default {
    components:{
        Thumbnail
    },
    // asyncData({env, params}){
    //     return client
    //         .getEntries(env.CTF_BLOG_POST_TYPE_ID)
    //         .then(entries =>{
    //         return {
    //             posts:entries.items
    //         }
    //         })
    //         .catch(console.error)
    // },
}
</script>

<style scoped>
.blog{
    padding:80px;
}
</style>