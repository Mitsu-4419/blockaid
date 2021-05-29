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
  <section class="topPage-skill-charts m-2">
    <div class="topPage-skill-title m-3">
      <p class='font-bold text-4xl'> Skills</p>
    </div>
    <div class="charts-wrapper my-3">
      <div class="chart mx-1.5">
        <radar-chart :chart-data="datacollection" :options="options"></radar-chart>
      </div>
      <div class="chart mx-1.5">
        <radar-chart :chart-data="datacollection1" :options="options1"></radar-chart>
      </div>
      <div class="chart mx-1.5">
        <radar-chart :chart-data="datacollection2" :options="options2"></radar-chart>
      </div>
    </div>
  </section>
  <section class="topPage-skill-charts m-2">
    <div class="topPage-skill-title m-3">
      <p class='font-bold text-4xl'> Portfolio</p>
    </div>
  </section>
  <section class="topPage-skill-charts m-2">
    <div class="topPage-skill-title m-3">
      <p class='font-bold text-4xl'> Blog</p>
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
            fontSize:18,
          },
          ticks: {
            min: 0,
            max: 5,
            stepSize: 1,
            display:false
          },
        },
        title:{
          display:true,
          fontSize:25,
          text:'Frontend'
        }, 
        legend: {
            display: false
         }
      },
      options1:{
        scale:{
          pointLabels:{
            fontSize:18,
          },
          ticks: {
            min: 0,
            max: 5,
            stepSize: 1,
            display:false
          },
        },
        title:{
          display:true,
          fontSize:25,
          text:'Backend'
        }, 
        legend: {
            display: false
         }
      },
      options2:{
        scale:{
          pointLabels:{
            fontSize:18,
          },
          ticks: {
            min: 0,
            max: 5,
            stepSize: 1,
            display:false
          },
        },
        title:{
          display:true,
          fontSize:25,
          text:'Others'
        }, 
        legend: {
            display: false
         }
      }
    }
  },
  methods: {
    RadarChart () {
        this.datacollection = {
            labels: ["Flutter", "Vue.js", "Contentful","GraphQL", "WASM", "Typescript","React.js"],
            datasets: [
                {
                    backgroundColor: 'red',
                    backgroundColor: this.fontColor.blue,
                    borderWidth: 1,
                    data: [4,5,5,3,2,3,3],
                    
                }
            ],
        },
        this.datacollection1 = {
            labels: ["Node.js", "Python", "Django","Solidity", "GCP", "Firebase","Solidity"],
            datasets: [
                {
                    backgroundColor: 'red',
                    backgroundColor: this.fontColor.green,
                    borderWidth: 1,
                    data: [3,4,3,3,3,4,3],
                    
                }
            ],
        },
        this.datacollection2 = {
            labels: ["Medical", "Statistics", "AtCoder","AI", "Kaggle","BlockChain"],
            datasets: [
                {
                    backgroundColor: 'red',
                    backgroundColor: this.fontColor.red,
                    borderWidth: 1,
                    data: [5,3,2,3,1,3],
                    
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
  },
  created(){
    this.RadarChart()
  },
}
</script>

<style>
.topPage-profile-bg{
  width: 100%;
  height:300px;
  background: rgb(218, 112, 112);
}
.topPage-skill-charts{
  width: 95%;
  margin-left: auto;
  margin-right:auto;
  background: rgb(179, 177, 177);
  padding:10px;
  height:500px;
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
