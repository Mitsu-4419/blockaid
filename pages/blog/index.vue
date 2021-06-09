<template>
    <section class='blog bg-gray-200 pt-100px flex justify-center grid grid-cols-10'>
        <section class='col-span-7 bg-red-200 p-5 flex justify-center'>
            <card 
                class='blog-card'
                v-for="(post, i) in posts" 
                :key="i"
                :title="post.fields.title"
                :id="post.sys.id"
                :content="post.fields.content"
                :postDate="post.fields.postDate"
                :mainThumbnail='post.fields.mainThumbnail.fields.file.url' 
            />
        </section>
        <section class='col-span-3 bg-green-200 p-10'>
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
    asyncData({env, params}){
        return client
            .getEntries(env.CTF_BLOG_POST_TYPE_ID)
            .then(entries =>{
                console.log(entries.items)

                console.log(entries.items[0].fields)
            return {
                posts:entries.items
            }
            })
            .catch(console.error)
    },
}
</script>

<style scoped>
.blog{
    padding:60px 80px;
}
.blog-card{
    width:45%
}
</style>