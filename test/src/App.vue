<script setup lang="ts">
import { usePlayer } from '@vue-motion/core';
import { defineComponent, onMounted } from 'vue';
import { createParser } from '@vue-motion/import';
import { Motion, Rect } from '@vue-motion/lib';

// import { defineAnimation, usePlayer, useWidget } from '@vue-motion/core'
// import { Line, Motion, Rect, Video, grow } from '@vue-motion/lib'
// import { onMounted, ref } from 'vue'
// import type { MathFunction } from '@vue-motion/extension-math'
// import type { BubbleChart } from '@vue-motion/extension-chart'
// import { BarChart, ChartData, ChartDataset, ChartUtil, LineChart, MixedChart } from '@vue-motion/extension-chart'
// import { DateTime, Duration } from 'luxon'
// import { Markdown } from '@vue-motion/extension-markdown'
// import { SpotLight, DistantLight } from '@vue-motion/extension-lights'

// // const fn1 = useWidget<InstanceType<typeof MathFunction>>('fn1')
// // const fn2 = useWidget<InstanceType<typeof MathFunction>>('fn2')
// // const fn3 = useWidget<InstanceType<typeof MathFunction>>('fn3')
// const line = useWidget<InstanceType<typeof BubbleChart>>('www')

// const x = ref(0)

// const change = defineAnimation((_context, progress) => {
//   x.value = progress * 4000
// })
const { parseTemplate, parseScript } = createParser(`
{
  "version": "0.6.0",
  "name": "Rotating Square",
  "description": "A square rotating 360 degrees",
  "widgets": [
    {
      "type": "Rect",
      "props": {
        "wid": {
          "type": "common",
          "value": "rotatingSquare"
        },
        "x": {
          "type": "common",
          "value": 200
        },
        "y": {
          "type": "common",
          "value": 200
        },
        "width": {
          "type": "common",
          "value": 100
        },
        "height": {
          "type": "common",
          "value": 100
        },
        "fill-color": {
          "type": "common",
          "value": "rgba(0, 150, 255, 0.7)"
        },
        "border-color": {
          "type": "common",
          "value": "rgba(0, 100, 200, 1)"
        },
        "border-width": {
          "type": "common",
          "value": 3
        }
      },
      "animations": [
        {
          "type": "preset",
          "preset": "rotate",
          "duration": 3,
          "props": {
            "offset": 1000
          }
        }
      ]
    }
  ],
  "reflects": {
    "a": 23333
  }
}
`)

const Test = defineComponent({
  template: parseTemplate(),
  ...parseScript()
})
console.log(Test.setup?.toString())
console.log(Test.template)

onMounted(() => {
  const { play } = usePlayer()

  // useAnimation(fn1)
  //   .animate(grow, { duration: 1 })
  // useAnimation(fn2)
  //   .animate(grow, { duration: 1 })
  // useAnimation(fn3)
  //   .animate(grow, { duration: 1 })

  play()
})
</script>

<template>
  <Motion id="motion" :width="1000" :height="1000">
    <!-- <Group>
         <NumberPlane :ranges-x="[-5, 5]" :ranges-y="[-5, 5]" :grid="false"/>
         <MathFunction :fn="(x) => Math.sin(x)" color="skyblue" :domain="[0, 0]" :ranges="[0, 5]" wid="fn1" />
         <MathFunction :fn="(x) => Math.cos(x)" color="red" :domain="[0, 0]" :ranges="[0, 5]" wid="fn2" />
         <MathFunction :fn="(x) => Math.tan(x)" color="green" :domain="[0, 0]" :ranges="[0, 5]" wid="fn3" />
       </Group>
       <Group>
         <NumberPlane :ranges-x="[0, 10]" :ranges-y="[0, 10]" />
       </Group> -->
    <!-- <MixedChart
      :labels="ChartUtil.dateSequence(
        DateTime.fromISO('2021-01-01').setLocale('en-US'),
        Duration.fromObject({ months: 4 }),
        'month',
        1,
      )"
      wid="chart1"
      index-axis="y"
    >
      <BarChart>
        <ChartDataset label="Bar1" :style="{ borderColor: '#f00', backgroundColor: '#f00' }">
          <ChartData :cross="1" />
          <ChartData :cross="2" />
          <ChartData :cross="0" />
          <ChartData :cross="1" />
        </ChartDataset>
        <ChartDataset label="Bar2" :style="{ borderColor: '#ff0', backgroundColor: '#ff0', borderRadius: 4, tension: 0.2 }">
          <ChartData :cross="2" />
          <ChartData :cross="1" />
          <ChartData :cross="3" />
          <ChartData :cross="2" />
          <ChartData :cross="1.5" :index="DateTime.fromISO('2021-03-15').setLocale('en-US')" :weight="10" />
    </ChartDataset>
      </BarChart>
      <LineChart>
        <ChartDataset label="Line1" :style="{ borderColor: '#00f', backgroundColor: '#00f' }">
          <ChartData :cross="1" />
          <ChartData :cross="2" />
          <ChartData :cross="0" />
          <ChartData :cross="1" />
        </ChartDataset>
        <ChartDataset label="Line2" :style="{ borderColor: '#0ff', backgroundColor: '#0ff', borderRadius: 4, tension: 0.2 }">
          <ChartData :cross="2" />
          <ChartData :cross="1" />
          <ChartData :cross="3" />
          <ChartData :cross="2" />
          <ChartData :cross="1.5" :index="DateTime.fromISO('2021-03-15').setLocale('en-US')" :weight="10" />
        </ChartDataset>
      </LineChart>
    </MixedChart> -->
    <!-- <DistantLight :color="color">
      <Markdown>
        # Hello world
        - 111
        - 222
        - 333
      </Markdown>
    </DistantLight>
    <Rect :width="100" :height="100" :fill-color="color"/>
    <Suspense>
      <Video href="./assets/output.mp4"/>
    </Suspense> -->
    <Test/>
  </Motion>
</template>
