<template>
  <div>
  <section class="topPage-profile-bg">
    <card 
        v-for="(post, i) in posts" 
        :key="i"
        :title="post.fields.title"
        :id="post.sys.id"
        :date="post.sys.updatedAt" 
    />
  </section>
  <section class="topPage-skill-charts">
    <div class="topPage-skill-title">
      <p> Skills</p>
    </div>
    <div class="charts-wrapper">
      <div class="chart">
        <radar-chart :chart-data="datacollection" :options="options"></radar-chart>
      </div>
      <div class="chart">
        
      </div>
      <div class="chart">
        
      </div>
    </div>
  </section>
  </div>
</template>

<script>
import Card from "~/components/Card.vue";
import {createClient} from "~/plugins/contentful.js"
import RadarChart from '../js/RadarChart.js'

const client = createClient()
export default {
  transition:'slide-left',
  components:{
    Card,
    RadarChart
  },
  data(){
    return{
      fontColor: {
          red: 'rgb(255, 99, 132,0.6)',
          orange: 'rgb(255, 159, 64,0.6)',
          yellow: 'rgb(255, 205, 86,0.6)',
          green: 'rgb(75, 192, 192,0.6)',
          blue: 'rgb(54, 162, 235,0.6)',
          purple: 'rgb(153, 102, 255,0.6)',
          grey: 'rgb(201, 203, 207,0.6)',
      },
      datacollection:null,
      options:{
        scale:{
          pointLabels:{
            fontSize:35,
          },
        },
        title:{
          display:true,
          fontSize:35,
          text:'好きな動物'
        },
      }
    }
  },
  created(){
    this.RadarChart()
  },
  methods: {
    RadarChart () {
        this.datacollection = {
            labels: ["夢", "希望", "未来","賢さ", "可愛さ", "素敵さ","人気"],
            datasets: [
                {
                    backgroundColor: 'red',
                    backgroundColor: this.fontColor.blue,
                    borderWidth: 1,

                    label: "どんべぇ売れ筋カラー",

                    data: [1, 40, 5,2, 7, 5,9]
                }
            ],
        }
    },
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
.topPage-profile-bg{
  width: 100%;
  height:300px;
  background: rgb(218, 112, 112);
}
.topPage-skill-charts{
  width: 90%;
  margin-left: auto;
  margin-right:auto;
  height:300px;
  background: rgb(179, 177, 177);
  padding:10px;
}
.topPage-skill-title{
  text-align: center;
  font-size: 25px;
}
.charts-wrapper{
  display: flex;
  justify-content: center;
}
.chart{
  width:33%;
  height:200px;
}
</style>
