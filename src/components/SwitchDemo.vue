<template>
<div>
  <h1>Switch 组件示例</h1>
  <Demo :component="Switch1Demo"></Demo>
  <Demo :component="Switch2Demo"></Demo>
  <span>下一节：</span>
  <router-link to="/doc/button" style="color: #0366d6">Button 组件</router-link>
</div>
</template>

<script lang="ts">
import Demo from './Demo.vue'
import {
  ref
} from 'vue'
import Switch1Demo from './Switch1.demo.vue'
import Switch2Demo from './Switch2.demo.vue'
export default {
  components: {
    Demo,
  },
  setup() {
    return {
      Switch1Demo,
      Switch2Demo,
    }
  },
}
</script>
