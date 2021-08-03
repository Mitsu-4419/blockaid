<template>
  <div class='block'>
    <section class="topPage-profile-bg">
      <div class='topPageImageWrapper'>
          <img src="../static/surgeon.png" alt="">
      </div>
    </section>
    <section class="topPage-skill-charts m-2">
      <div class="topPage-skill-title m-3">
        <p class='font-bold text-4xl'> Skills</p>
      </div>
      <div class="charts-wrapper my-3">
        <div class="chart">
          <radar-chart :chart-data="datacollection" :options="options"></radar-chart>
        </div>
        <div class="chart">
          <radar-chart :chart-data="datacollection1" :options="options1"></radar-chart>
        </div>
        <div class="chart">
          <radar-chart :chart-data="datacollection2" :options="options2"></radar-chart>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
// import Card from "~/components/Card.vue";
import {createClient} from "~/plugins/contentful.js"
import RadarChart from '../js/RadarChart.js'

const client = createClient()
export default {
  transition:'slide-left',
  components:{
    // Card,
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
            fontSize:16,
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
            fontSize:16,
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
            fontSize:16,
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
            labels: ["Vue/nuxt","Tailwind","Flutter","GraphQL", "WASM", "Typescript","React.js"],
            datasets: [
                {
                    backgroundColor: 'red',
                    backgroundColor: this.fontColor.blue,
                    borderWidth: 1,
                    data: [5,4,4,3,2,4,4],
                    
                }
            ],
        },
        this.datacollection1 = {
            labels: ["Node.js", "Python", "Django","C,C++", "GCP", "Firebase","Solidity"],
            datasets: [
                {
                    backgroundColor: 'red',
                    backgroundColor: this.fontColor.green,
                    borderWidth: 1,
                    data: [4,4,4,2,4,5,3],
                    
                }
            ],
        },
        this.datacollection2 = {
            labels: ["Medical", "Statistics", "Docker","AI", "DataScience","BlockChain"],
            datasets: [
                {
                    backgroundColor: 'red',
                    backgroundColor: this.fontColor.red,
                    borderWidth: 1,
                    data: [5,3,3,3,3,3],
                    
                }
            ],
        }
    },
  },
  asyncData({env, params}){
    return client
    .getEntries(env.CTF_BLOG_POST_TYPE_ID)
    .then(entries =>{
      console.log("コンテントフルとつながったよ")
      console.log(entries.items)
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
  width: 95%;
  height:400px;
  margin-left: auto;
  margin-right: auto;
  margin-top:20px;
  margin-bottom:20px;
  display: flex;
  justify-content: center;
  align-items: center;
  /* background: rgb(218, 112, 112); */
}
.topPageImageWrapper{
  display: flex;
  justify-content:center;
  width: 260px;
  height:260px;
}
.topPage-skill-charts{
  width: 95%;
  margin-left: auto;
  margin-right:auto;
  /* background: rgb(179, 177, 177); */
  padding:10px;
  /* height:500px; */
}
.topPage-skill-title{
  text-align: center;
  font-size: 25px;
}
.charts-wrapper{
  display: flex;
  justify-content: center;
  margin-top:30px
}
.chart{
  width:280px;
  height:280px;
  margin:10px 20px 10px 20px;
}
</style>
