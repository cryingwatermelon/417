<script lang="ts" setup>
import * as echarts from 'echarts'

const charts = ref()
onMounted(() => {
  const mychart = echarts.init(charts.value)
  mychart.setOption({
    title: {
      text: '景区排行',
      link: 'http://www.baidu.com',
      left: '50%',
      textStyle: {
        color: 'yellowgreen',
        fontSize: 20,
      },
      subtext: '各大景区排行',
      subtextStyle: {
        color: 'yellowgreen',
        fontSize: 16,
      },
    },
    xAxis: {
      type: 'category',
    },
    yAxis: {},
    grid: {
      left: 20,
      bottom: 20,
      right: 20,
    },
    series: [{
      type: 'bar',
      data: [10, 20, 30, 40, 50, 60, 70],
      // 柱状图的文本标签
      label: {
        show: true,
        position: 'insideTop',
        color: 'yellowgreen',
      },
      showBackground: true,
      backgroundStyle: {
        color: {
          type: 'linear',
          x: 0,
          y: 0,
          x2: 0,
          y2: 1,
          colorStops: [{
            offset: 0,
            color: 'white',
          }, {
            offset: 1,
            color: 'blue',
          }],
          global: false,
        },
      },
      itemStyle: {
        borderRadius: [10, 10, 0, 0],
        color(data: any) {
          const arr = ['red', 'orange', 'yellow', 'green', 'purple', 'hotpink', 'skyblue']
          return arr[data.dateIndex]
        },
      },

    }],
    tooltip: {
      backgroundColor: 'rgba(50,50,50,0.7)',
    },
  })
})
</script>

<template>
  <div class="box6">
    <div class="title">
      <p>热门景区</p>
      <img src="../../images/dataScreen-title.png" alt="">
    </div>
    <!-- 图形图标的容器 -->
    <div ref="charts" class="charts" />
  </div>
</template>

<style lang="scss" scoped>
.box6{
  width: 100%;
  height: 100%;
  background: url(../../images/dataScreen-main-cb.png)no-repeat;
  background-size: 100% 100%;
  margin: 20px,20px;
  .title{
  margin-left: 5px;
  p{
    color: white;
    font-size: 20px;

  }
  }
  .charts{
    height: calc(100% - 30%);
  }
}
</style>
