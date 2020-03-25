<template>
  <div id="app">
    <!-- Header -->
    <header class="header">
      <!-- Header Logo  -->
      <div class="left-header">
        <a href="#" class="logo">
          <img src="./assets/img/logo.png" alt class="logo-img" />
        </a>
      </div>
      <!-- Header Navigation  -->
      <div class="right-header">
        <!-- Top Navigation -->
        <div class="top-navigation-wrap">
          <nav class="header-top-navigation">
            <a href="#">Über uns</a>
            <a href="#">Redaktion</a>
          </nav>
          <!-- Language Swither -->
          <div class="language-switch">
            <button class="deutch-lang active">de</button>
            <button class="english-lang">en</button>
          </div>
        </div>
        <!-- Bottom Navigation -->
        <div class="bottom-navigation-wrap">
          <input class="header-search-input" type="text" />
          <nav class="header-bottom-navigation" v-bind:class="{ show: isHidden }">
            <span class="hide-on-mobile">|</span>
            <a href="#">Design+lifestyle</a>
            <span class="hide-on-mobile">|</span>
            <a href="#">Trends</a>
            <span class="hide-on-mobile">|</span>
            <a href="#">Infodelight</a>
            <span class="hide-on-mobile">|</span>
            <a href="#">Smart Living</a>
          </nav>
        </div>
      </div>
      <!-- Mobile Navigation Button-->
      <div class="mobile-nav-btn" v-on:click="isHidden = !isHidden">
        <div></div>
        <div></div>
        <div></div>
      </div>
    </header>
    <!-- First Section -->
    <section class="first-section">
      <div class="left-part">
        <Slider />
      </div>
      <div class="right-part">
        <!-- Welcome Widget -->
        <div class="welcome-widget-wrap">
          <div class="welcome-widget">
            <div class="title">A place called Inspiration.</div>
            <div class="description">
              Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet,
              consectetur, adipisci velit, sed quia non numquam eius modi
              tempora incidunt ut labore et dolore magnam voluptatem.
            </div>
            <button href="#" class="about-link" @click="addChart(chartType)">Insert</button>
            <!-- Select -->
            <select class="selectChartType" v-model="chartType">
              <option
                v-for="option in chartTypeSelectOptions"
                v-bind:value="option.value"
                v-bind:key="option.value"
              >{{ option.text }}</option>
            </select>
          </div>
        </div>
      </div>
    </section>
    <!-- News Section -->
    <section class="news-section">
      <article class="news-article first-article">
        <div class="article-wrap">
          <div class="keywords">| Design+Lifestyle | Smart Living |</div>
          <h2 class="title">
            Was hilft mir, Energie zu sparen und Spaß zu haben, bei mir zu
            Hause?
          </h2>
          <p class="description">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut dolor in reprehenderit in quia...
          </p>
        </div>
      </article>
      <article class="news-article second-article">
        <div class="article-wrap">
          <div class="keywords">| Design+Lifestyle | Smart Living |</div>
          <h2 class="title">
            Was hilft mir, Energie zu sparen und Spaß zu haben, bei mir zu
            Hause?
          </h2>
          <p class="description">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do
            eiusmod tempor incididunt ut dolor in reprehenderit in quia...
          </p>
        </div>
      </article>
    </section>
    <!-- Charts Section -->
    <section class="chart-section">
      <!-- Chart Item -->
      <div class="chart-item" v-for="(item, index) in chartsArr" v-bind:key="index">
        <chart :options="item"></chart>
      </div>
    </section>
  </div>
</template>

<script>
import Slider from "./components/Slider.vue";
import { Chart } from "highcharts-vue";

export default {
  name: "App",
  components: {
    Slider,
    chart: Chart
  },
  data() {
    return {
      chartType: "pie",
      isHidden: false, // Mobile navigation triger
      chartsArr: [], // charts Array
      chartTypeSelectOptions: [
        // list of chart types for input type select
        { text: "Bar", value: "bar" },
        { text: "Line", value: "line" },
        { text: "Pie", value: "pie" }
      ],
      // Chart options for Bar and line. May be used for other types of charts
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
          type: "pie"
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
      },
      // Chart options for Pie
      pieChartOptions: {
        title: {
          text: `Points Scored`,
          y: 40,
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
            center: ["50%", "0"],
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
          align: "center",
          y: 20,
          x: 180,
          verticalAlign: "top",
          padding: 20,
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
  },
  methods: {
    addChart(chartType) {
      // Add new Chart
      if (chartType) {
        let optionsCopy; // variable for copying chart options
        if (chartType != "pie") {
          optionsCopy = JSON.parse(JSON.stringify(this.chartOptions)); //  copying chartOptions
        } else {
          optionsCopy = JSON.parse(JSON.stringify(this.pieChartOptions)); //  copying pieChartOptions
        }
        optionsCopy.chart.type = chartType; // add selected chart type
        this.chartsArr.push(optionsCopy); // push new chart options to 'chartsArr'
      } else console.log("empty value");
    }
  }
};
</script>

<style lang="sass">
 /* Import PT Sans Google font instead of "Verdana" and
 import Muli Google font instead of "Linotype"
 */
@import url('https://fonts.googleapis.com/css?family=Muli:400,700|PT+Sans:400,700&display=swap')

// Import main styles
@import "./sass/index.sass"
</style>
