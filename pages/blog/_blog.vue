<template>
  <h1>hogehoge</h1>
</template>

<script>
import { documentToHtmlString } from '@contentful/rich-text-html-renderer'
import { createClient } from '~/plugins/contentful.js'

const client = createClient()
export default {
  // data(){
  //   return{
  //     query:''
  //   }
  // },
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
