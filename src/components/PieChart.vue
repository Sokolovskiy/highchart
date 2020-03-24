<template id="pie-chart">
  <div class="">
    <highcharts :options="chartOptions"></highcharts>
  </div>
</template>

<script>
import { Chart } from "highcharts-vue";

export default {
  name: "PieChart",
  components: {
    highcharts: Chart
  },
  template: "#pie-chart",
  data() {
    return {
      chartOptions: {
        title: {
          text: `Points Scored`,
          x: -120,
          y: 50,
          style: {
            color: "#000000",
            fontWeight: "bold"
          }
        },
        chart: {
          type: `pie`
        },
        plotOptions: {
          pie: {
            size: 300,
            center: [200, 150],
            allowPointSelect: true,
            cursor: "pointer",
            dataLabels: {
              enabled: false,
              format: "{point.percentage:.1f} %",
              color: "#ffffff",
              crop: false,
              style: {
                fontSize: "14px",
                fontWeight: "normal"
              }
            },
            showInLegend: true
          }
        },
        legend: {
          layout: "vertical",
          align: "right",
          verticalAlign: "top",
          padding: 100,
          itemMarginTop: 2,
          itemMarginBottom: 0,
          enabled: true
        },
        series: [
          {
            name: "Teams",
            colorByPoint: true,
            dataLabels: {
              enabled: true,
              inside: true,
              distance: "-35%"
            },
            data: [
              {
                name: "Team 1",
                color: "#5f97f6",
                y: 21.8
              },
              {
                name: "Team 2",
                color: "#dc4437",
                y: 32.7
              },
              {
                name: "Team 3",
                color: "#efa705",
                y: 10.9
              },
              {
                name: "Team 4",
                color: "#109d58",
                y: 34.5
              }
            ]
          }
        ],
        responsive: {
          rules: [
            {
              condition: {
                maxWidth: 550,
                minWidth: 320
              },
              chartOptions: {
                legend: {
                  enabled: false
                },
                title: {
                  x: 0,
                  y: 30,
                  align: "center"
                },
                plotOptions: {
                  pie: {
                    center: ["50%", "50%"]
                  }
                }
              }
            }
          ]
        }
      }
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass"></style>
