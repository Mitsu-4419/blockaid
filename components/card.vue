<template>
    <nuxt-link :to="`/blog/${id}`" >
      <div class="wrapper rounded overflow-hidden shadow-lg mx-2 my-2 ">
        <img class="w-full thumnail-img" :src="mainThumbnail" alt="Sunset in the mountains">
        <div class="px-6 py-2">
          <div class="font-bold text-xl mb-2">{{title}}</div>
          <!-- <p class="text-gray-700 text-base">
            <div v-html="toHtmlString(content)"></div>
          </p> -->
        </div>
        <div class="px-6 py-2">
          <Tag tag="hoge"/>
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#photography</span>
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#travel</span>
          <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#winter</span>
        </div>
      </div>
    </nuxt-link>
</template>
<script>
import Tag from '~/components/Tag.vue'
import { documentToHtmlString } from '@contentful/rich-text-html-renderer'
export default{
    components:{
        Tag
    },
    props:{
        title:{
            type:String,
            default:''
        },
        id:{
            type:String,
            default:''
        },
        content:{
            JSON
        },
        mainThumbnail:{
          type:String,
          default:''
        }
    },
    methods:{
      toHtmlString(obj){
        return documentToHtmlString(obj)
      }
    }
}
</script>

<style scoped>
.thumnail-img{
  height: 200px;
}
.wrapper{
  height:300px;
}
</style>
