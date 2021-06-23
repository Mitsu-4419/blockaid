<template>
    <section class='p-16 bg-gray-100  grid grid-cols-10 min-h-screen'>
        <section class='col-span-7 bg-red-200 p-5 grid grid-cols-2 gap-2 grid-rows-3'>
            <card 
                v-for="(post, i) in posts" 
                :key="i"
                :title="post.fields.title"
                :id="post.sys.id"
                :content="post.fields.content"
                :postDate="post.fields.postDate"
                :mainThumbnail='post.fields.mainThumbnail.fields.file.url' 
            />
        </section>
        <section class='col-span-3 bg-green-200 '>
            <img class="w-full" src="../../assets/images/sakurajima.JPG" alt="">
            <div class="w-28 h-28 mx-auto -mt-12 z-30 rounded-full">
              <img class='w-full m-auto' src="../../assets/images/koro.png" alt="">
            </div>
            <div class='flex justify-center mt-3'>
                <section class="text-3xl font-bold">Ko-rin</section>
            </div>
            <div class="p-2 mt-2">
                <p>元心臓外科医。35歳からプログラミングを学んで現在鹿児島でエンジニアをしています。
                    主戦場はFrontですが、技術全般好きです。技術、趣味など気ままに書いていきます。
                </p>
            </div>
            <!-- 最新記事Box -->
            <div class='mt-20'>
                <div class='h-15 bg-blue-700 flex items-center p-2'>
                   <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-3" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M17.707 9.293a1 1 0 010 1.414l-7 7a1 1 0 01-1.414 0l-7-7A.997.997 0 012 10V5a3 3 0 013-3h5c.256 0 .512.098.707.293l7 7zM5 6a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
                    </svg>
                    <div class='text-white font-bold text-lg'>最新記事！</div>
                </div>
                <div v-for="(post, i) in posts" :key="i">
                    <div class='flex p-4 items-center'>
                        <img :src="post.fields.mainThumbnail.fields.file.url" alt="" class='w-16 h-16'>
                        <span class='ml-3'>{{post.fields.title}}</span>
                    </div>
                </div>
            </div>
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

</style>