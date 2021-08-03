<template>
    <section class='p-16 bg-gray-100  grid grid-cols-10 min-h-screen'>
        
        <section class="bg-white w-100% col-span-7 pt-3 pb-2 shadow" >
            <nav class="flex justify-center flex-col sm:flex-row">
                <button class="text-gray-600 w-25% py-4 px-6 block font-bold  focus:text-white focus:bg-gradient-to-r from-purple-200 to-blue-300 focus:outline-none text-gray-100 border-b-2 font-medium border-none">
                    初めまして
                </button>
                <button class="text-gray-600 w-25% py-4 px-6 block font-bold  focus:text-white focus:bg-gradient-to-r from-purple-200 to-blue-300 focus:outline-none text-gray-100 border-b-2 font-medium border-none">
                    勉強
                </button>
                <button class="text-gray-600 w-25% py-4 px-6 block font-bold  focus:text-white focus:bg-gradient-to-r from-purple-200 to-blue-300 focus:outline-none text-gray-100 border-b-2 font-medium border-none">
                    鹿児島生活
                </button>
                <button class="text-gray-600 w-25% py-4 px-6 block font-bold  focus:text-white focus:bg-gradient-to-r from-purple-200 to-blue-300 focus:outline-none text-gray-100 border-b-2 font-medium border-none">
                    趣味
                </button>
            </nav>
        </section>
        <section class='bg-gray-100 w-100% col-span-7 h-10'>

        </section>
        <section class='col-span-7 bg-white p-5 grid grid-cols-1 gap-4 md:grid-cols-2 xl:grid-cols-3 xl:grid-rows-3 xl:row-span-1'>
            <card 
                v-for="(post, i) in posts" 
                :key="i"
                :title="post.fields.title"
                :id="post.sys.id"
                :content="post.fields.content"
                :postDate="post.fields.postDate"
                :tag="post.fields.tag"
                :mainThumbnail='post.fields.mainThumbnail.fields.file.url' 
            />
        </section>
        
        
        <section class='col-span-3 pl-2'>
            <div class='shadow '>
                <img class="w-full" src="../../assets/images/sakurajima.JPG" alt="">
                <div class="w-28 h-28 mx-auto -mt-12 z-30 rounded-full">
                <img class='w-full m-auto' src="../../assets/images/koro.png" alt="">
                </div>
                <div class='flex justify-center mt-3'>
                    <section class="text-3xl font-bold">Ko-rin</section>
                </div>
                <div class="p-4 mt-2 text-sm">
                    <p>元心臓外科医。35歳からプログラミングを学んで現在鹿児島でエンジニアをしています。
                        主戦場はFrontですが、技術全般好きでDataScience, ML, AIも勉強しています。<br/>
                        プログラミング、趣味、鹿児島生活など気ままに書いていきます。
                    </p>
                </div>
            </div>
            <!-- 最新記事Box -->
            <div class='mt-20 bg-white shadow'>
                <div class='h-15 bg-blue-700 flex items-center p-2'>
                   <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-3" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M17.707 9.293a1 1 0 010 1.414l-7 7a1 1 0 01-1.414 0l-7-7A.997.997 0 012 10V5a3 3 0 013-3h5c.256 0 .512.098.707.293l7 7zM5 6a1 1 0 100-2 1 1 0 000 2z" clip-rule="evenodd" />
                    </svg>
                    <div class='text-white font-bold text-lg'>最新記事！</div>
                </div>
                <div v-for="(post, i) in posts" :key="i">
                    <div v-if='i<5'>
                        <div class='flex p-2 items-center'>
                            <img :src="post.fields.mainThumbnail.fields.file.url" alt="" class='w-16 h-16'>
                            <span class='ml-3'>{{post.fields.title}}</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class='bg-red-100 w-100% col-span-7 h-10'>
            <Pagenation/>
        </section>
    </section>
</template>

<script>
import Thumbnail from '~/components/blog/Thumbnail.vue'
import {createClient} from "~/plugins/contentful.js"
import Pagenation from '../../components/pagination.vue'
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
                entries.items.sort(function(a,b){
                    const dateA = a.fields.postDate
                    const dateB= b.fields.postDate
                    
                    if (dateA>dateB){
                        return -1
                    }else if(dateA<dateB){
                        return 1
                    }
                })
                return{
                   posts:entries.items
                }
            })
            .catch(console.error)
    },
}
</script>

<style scoped>

</style>
