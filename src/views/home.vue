<template>
  <div class="home-view">
    <layout-box title="组件" description="使用组件的详细描述。">
      <component-name></component-name>
    </layout-box>

    <layout-box title="操作" description="点击下方按钮查看不同的效果。" style="margin-top: 16px">
      <a-button type="primary" @click="onOpenVueTour()">vue-tour</a-button>
      <a-button type="primary" style="margin: 0 10px" @click.stop="onOpenDriver()">driver.js</a-button>
      <a-button type="primary" @click="onOpenShepherd()">shepherd.js</a-button>
    </layout-box>

    <v-tour name="myTour" :steps="steps"></v-tour>
  </div>
</template>

<script>
import Vue from 'vue'
import Shepherd from '@/components/shepherd'

import VueTour from 'vue-tour'
import 'vue-tour/dist/vue-tour.css'

import Driver from 'driver.js'
import 'driver.js/dist/driver.min.css'

Vue.use(VueTour)
Vue.use(Shepherd)

export default {
  data () {
    return {
      steps: [{
        target: '#logo',
        content: '这是一个引导提示，这是一个引导提示，这是一个引导提示，这是一个引导提示。'
      }]
    }
  },
  methods: {
    onOpenVueTour () {
      this.$tours.myTour.start()
    },
    onOpenDriver () {
      const driver = new Driver({
        doneBtnText: '完成',
        closeBtnText: '关闭',
        stageBackground: '#ffffff',
        nextBtnText: '下一步',
        prevBtnText: '上一步'
      })
      driver.defineSteps([{
        element: '#logo',
        popover: {
          title: '引导提示 - shepherd.js',
          description: '这是一个引导提示，这是一个引导提示，这是一个引导提示，这是一个引导提示。'
        }
      }])
      driver.start()
    },
    onOpenShepherd () {
      const shepherd = this.$shepherd({
        steps: [{
          attachTo: {
            element: document.querySelector('#logo'),
            on: 'bottom'
          },
          title: '引导提示 - shepherd.js',
          text: '这是一个引导提示，这是一个引导提示，这是一个引导提示，这是一个引导提示。',
          buttons: [{
            action () {
              return this.complete()
            },
            text: '关闭'
          }]
        }]
      })
      shepherd.start()
    }
  }
}
</script>
