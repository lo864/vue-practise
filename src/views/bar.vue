<!--
 * @Author: lost_3stars jiangguangxin@cmict.chinamobile.com
 * @Date: 2025-05-13 23:17:10
 * @LastEditors: lost_3stars jiangguangxin@cmict.chinamobile.com
 * @LastEditTime: 2025-05-14 00:34:04
 * @FilePath: \vue-practise\src\views\bar.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup>
import * as echarts from 'echarts';
import { ref, onMounted } from 'vue'
const echart = ref()
onMounted(() => {
  const chartDom = echart.value;
  const myChart = echarts.init(chartDom);
  let option
  option = {
    // 标题配置
    title: {
      text: '参会率',      // 标题文本
      textAlign: 'center',   // 文字水平居中
      left: '50%',           // 标题容器水平居中（配合 textAlign 使用）
      bottom: '20%',            // 距离底部 10 像素（数值或百分比，如 '5%'）
      textStyle: {
        fontSize: 26,        // 字体大小
        color: '#333'        // 字体颜色
      }
    },
    series: [
      {
        type: 'gauge',
        startAngle: 225, // 起始角度
        endAngle: -45, // 结束角度
        radius: '90%', // 环的半径
        axisLine: {
          lineStyle: {
            width: 0 // 环的宽度
          }
        },
        progress: {
          show: true,
          width: 40,
          roundCap: true, // 进度条端点圆角
          itemStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [
              { offset: 0, color: '#f77068' }, // 进度条渐变起始色（蓝色）
              { offset: 1, color: '#52a8e0' } // 进度条渐变结束色（深蓝）
            ])
          }
        },
        pointer: { show: false },
        // pointer: {
        //   icon: 'circle',
        //   length: '10%',
        //   width: 40, // 圆点大小
        //   itemStyle: {
        //     color: '#FF0000',
        //     shadowColor: 'rgba(0,0,0,0)'
        //   },
        //   offsetCenter: ['0%', '-80%']
        // },
        axisTick: {
          show: true,
          splitNumber: 10,
          lineStyle: {
            color: '#f5989f',     // 主刻度线颜色
            width: 3
          },
          length: 20
        }, // 隐藏刻度
        splitLine: { show: false }, // 隐藏分割线
        axisLabel: { show: false }, // 隐藏标签
        detail: {
          valueAnimation: true,
          formatter: '{value}%',
          fontSize: 40,
          color: '#333',
          offsetCenter: [0, 0] // 文本居中
        },
        data: [{ value: 95 }]
      },
      {
        type: 'gauge',
        startAngle: 225,
        endAngle: -45,
        radius: `80%`, // 内环半径紧贴外环
        center: ['50%', '50%'],
        axisLine: {
          lineStyle: {
            width: 0
          }
        },
        progress: {
          show: true,
          width: 80,
          itemStyle: {
            color: new echarts.graphic.RadialGradient(
              0.5, 0.5, 1, // 中心点 (x, y, r)，相对于图表区域
              [
                { offset: 0, color: '#fef0f0' }, // 圆心颜色（红色）
                { offset: 1, color: '#fff' }  // 外径颜色（橙色）
              ]
            )
          }
        },
        pointer: { show: false },
        axisTick: { show: false },
        splitLine: { show: false },
        axisLabel: { show: false },
        detail: { show: false }, // 内环不显示数字
        data: [{ value: 95 }]
      }
    ]
  };

  option && myChart.setOption(option);
});
</script>

<template>
  <div ref="echart" style="width: 800px;height: 800px;"></div>
</template>

<style></style>
