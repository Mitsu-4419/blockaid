<template>
    <nuxt-link :to="`/blog/${id}`" class="card">
        <img class="w-full h-32 sm:h-48 object-cover" :src="mainThumbnail" alt="Sunset in the mountains">
        <div class="px-6 py-2">
          <div class="flex items-center my-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
            <span class='text-gray-400 text-sm ml-2'>{{posted}}</span>
          </div>
          <div class="font-bold text-xl mb-2 mt-2">{{title}}</div>
        </div>
        <Tag :tag="tag"/>
    </nuxt-link>
</template>
<script>
import Tag from '~/components/Tag.vue'
import { documentToHtmlString } from '@contentful/rich-text-html-renderer'
export default{
    data(){
      return{
        posted:""
      }
    },
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
        },
        postDate:{
          type:String,
          default:''
        },
        tag:{
          type:String,
          default:''
        }
    },
    methods:{
      toHtmlString(obj){
        return documentToHtmlString(obj)
      },
      getStringFromDate(date) {
        date = new Date(date)
        var year_str = date.getFullYear();
        //月だけ+1すること
        var month_str = 1 + date.getMonth();
        var day_str = date.getDate();
        
        format_str = 'YYYY年MM月DD日';
        format_str = format_str.replace(/YYYY/g, year_str);
        format_str = format_str.replace(/MM/g, month_str);
        format_str = format_str.replace(/DD/g, day_str);
        
        return format_str;
        }
    },
    mounted(){
      if(this.postDate){
        const a =this.postDate.split('T')[0]
        const tmp=a.split("-")
        if (tmp[1][0]=="0") tmp[1]=tmp[1][1]
        this.posted=tmp[0]+"年"+tmp[1]+"月"+tmp[2]+"日"
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
.card {
  @apply bg-white rounded overflow-hidden shadow-md relative max-h-80 hover:shadow-xl;
}

</style>
