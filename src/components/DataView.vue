<template>
  <div>
    Age and Gender Distribution of Data
   
    <canvas id="bar-chart"></canvas>
    <canvas id="line-chart"></canvas>
  </div>
</template>

<script>
import Chart from "chart.js";
import { testData } from "../testData.js";
var ageDist = [0, 0, 0, 0];
var maleAgeDist = [0, 0, 0, 0];
var femaleAgeDist = [0, 0, 0, 0];
export default {
  methods: {
    createChart(chartId, chartData,type) {
      const ctx = document.getElementById(chartId);
      const myChart = new Chart(ctx, {
        type: type,
        data: chartData.data,
        options: chartData.options,
      });
      return myChart;
    },
    analysisData(testData) {
      console.log(testData);
      console.log(testData.length);
      for (var i = 0; i < testData.length; i++) {
        if (testData[i].age > 0 && testData[i].age <= 14) {
          ageDist[0] = ageDist[0] + 1;
          if (testData[i].gender === "Male") {
            maleAgeDist[0] = maleAgeDist[0] + 1;
          } else {
            femaleAgeDist[0] = femaleAgeDist[0] + 1;
          }
        } else if (testData[i].age > 14 && testData[i].age <= 19) {
          ageDist[1] = ageDist[1] + 1;
          if (testData[i].gender === "Male") {
            maleAgeDist[1] = maleAgeDist[1] + 1;
          } else {
            femaleAgeDist[1] = femaleAgeDist[1] + 1;
          }
        } else if (testData[i].age > 19 && testData[i].age <= 64) {
          ageDist[2] = ageDist[2] + 1;
          if (testData[i].gender === "Male") {
            maleAgeDist[2] = maleAgeDist[2] + 1;
          } else {
            femaleAgeDist[2] = femaleAgeDist[2] + 1;
          }
        } else {
          ageDist[3] = ageDist[3] + 1;
          if (testData[i].gender === "Male") {
            maleAgeDist[3] = maleAgeDist[3] + 1;
          } else {
            femaleAgeDist[3] = femaleAgeDist[3] + 1;
          }
        }
      }
      console.log(ageDist);
      console.log(maleAgeDist);
      console.log(femaleAgeDist);
   
    },
  },
  data() {
    return {
        selected:'',
      testData: {
        type: "bar",
        data: {
          labels: ["Children", "Youth", "Adults", "Seniors"],
          datasets: [
            {
              // one line graph
              label: "Age distribution",
              data: ageDist,
              backgroundColor: [
                "rgba(255,255,0,.5)", // yellow
                "rgba(255,255,0,.5)",
                "rgba(255,255,0,.5)",
                "rgba(255,255,0,.5)",
              ],
              borderColor: ["#FFFF00", "#FFFF00", "#FFFF00", "#FFFF00"],
              borderWidth: 3,
            },
            {
              // another line graph
              label: "Gender Distributon - Male",
              data: maleAgeDist,
              backgroundColor: [
                "rgb(0, 0, 255,.5)",
                "rgb(0, 0, 255,.5)",
                "rgb(0, 0, 255,.5)",
                "rgb(0, 0, 255,.5)", // blue - male
              ],
              borderColor: ["#0000FF", "#0000FF", "#0000FF", "#0000FF"],
              borderWidth: 3,
            },
            {
              // another line graph
              label: "Gender Distributon - Female",
              data: femaleAgeDist,
              backgroundColor: [
                "rgba(255,182,193,.5)",
                "rgba(255,182,193,.5)",
                "rgba(255,182,193,.5)",
                "rgba(255,182,193,.5)", // pink - female
              ],
              borderColor: ["#FFB6C1", "#FFB6C1", "#FFB6C1", "#FFB6C1"],
              borderWidth: 3,
            },
          ],
        },
        options: {
          responsive: true,
          lineTension: 1,
          scales: {
            yAxes: [
              {
                ticks: {
                  beginAtZero: true,
                  padding: 25,
                },
              },
            ],
          },
        },
      },
    };
  },
  mounted() {
    this.analysisData(testData);
    this.createChart("bar-chart", this.testData,"bar");
    this.createChart("line-chart", this.testData,"line");
   
  },

};
</script>
