<template>
  <section class='blog bg-gray-200 pt-100px flex justify-center grid grid-cols-10'>
        <section class='col-span-7 bg-red-200 p-5' v-if="content">
            <div>{{content.fields.title}}</div>
            <div>{{content.fields.postDate}}</div>
            <div>
              <img :src="content.fields.mainThumbnail.fields.file.url" alt="">
            </div>
            <p class="text-gray-700 text-base">
              <div v-html="toHtmlString(content.fields.content)"></div>
            </p>
        </section>
        <section class='col-span-3 bg-green-200 p-10'>
        </section>
    </section>
</template>

<script>
import { documentToHtmlString } from '@contentful/rich-text-html-renderer'
import { createClient } from '~/plugins/contentful.js'

const client = createClient()
export default {
  data(){
    return{
      content:''
    }
  },
  methods: {
    toHtmlString(obj) {
      return documentToHtmlString(obj)
    },
    // setQuery(){
    //   console.log(this.$route.params.blog)
    //   this.query = this.$route.params.blog || ''
    //   console.log(this.query)
    // },
  },
  async created(){
    const id = this.$route.params.blog
    const place = await client.getEntry(id)
    console.log(place)
    this.content=place
  },
  
}
// import { documentToHtmlString } from '@contentful/rich-text-html-renderer'

// export default {
//     props:{
//         title:{
//             type:String,
//             default:''
//         },
//         id:{
//             type:String,
//             default:''
//         },
//         content:{
//             JSON
//         },
//         mainThumbnail:{
//           type:String,
//           default:''
//         }
//     },
//     methods:{
//       toHtmlString(obj){
//         return documentToHtmlString(obj)
//       }
//     }
// }
</script>

<style scoped>
.blog{
  padding:60px 80px;
}
</style>