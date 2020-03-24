<template id="custom-chart">
  <div class="">
    <!-- Select -->
    <select v-model="chartType">
      <option
        v-for="option in chartTypeSelectOptions"
        v-bind:value="option.value"
        v-bind:key="option.value"
      >
        {{ option.text }}
      </option>
    </select>
    <!-- Chart -->
    <highcharts :options="chartOptions"></highcharts>
  </div>
</template>

<script>
import { Chart } from "highcharts-vue";

export default {
  name: "CustomChart",
  components: {
    highcharts: Chart
  },
  template: "#custom-chart",
  data() {
    return {
      chartTypeSelectOptions: [
        { text: "Bar", value: "bar" },
        { text: "Line", value: "line" }
      ],
      chartType: "bar",
      chartOptions: {
        title: {
          text: `Points Scored`,
          align: "left",
          x: 50,
          y: 30,
          style: {
            color: "#000000",
            fontWeight: "bold"
          }
        },
        chart: {
          type: "bar"
        },
        plotOptions: {
          bar: {
            dataLabels: {
              enabled: false
            }
          },
          series: {
            pointPadding: 0.04,
            groupPadding: 0.15,
            borderWidth: 0,
            shadow: false
          }
        },
        xAxis: {
          categories: ["Team 1", "Team 2", "Team 3", "Team 4"],
          title: {
            text: null
          }
        },
        yAxis: {
          min: 0,
          max: 100,
          title: {
            text: "",
            align: "high"
          },
          labels: {
            overflow: "justify"
          }
        },
        legend: {
          layout: "vertical",
          align: "right",
          verticalAlign: "top",
          y: 40,
          itemMarginTop: 2,
          width: "16%",
          itemMarginBottom: 0,
          symbolWidth: 30,
          symbolHeight: 15,
          symbolRadius: 0,
          squareSymbol: false
        },
        series: [
          {
            name: "Period 1",
            data: [24, 36, 13, 34],
            color: "#5c9af1"
          },
          {
            name: "Period 2",
            data: [84, 24, 34, 62],
            color: "#214488"
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
                  align: "center"
                }
              }
            }
          ]
        }
      }
    };
  },
  watch: {
    chartType(newValue) {
      this.chartOptions.chart.type = newValue.toLowerCase();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass"></style>
