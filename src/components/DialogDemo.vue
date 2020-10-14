<template>
<h1>Dialog 示例</h1>
<Demo :component="Dialog1Demo" />
<Demo :component="Dialog2Demo" />
<span>下一节：</span>
<router-link to="/doc/tabs" style="color: #0366d6">Tabs 组件</router-link>
</template>

<script lang="ts">
import Demo from './Demo.vue'
import Dialog1Demo from './Dialog1.demo.vue'
import Dialog2Demo from './Dialog2.demo.vue'
export default {
  components: {
    Demo,
  },
  setup() {
    return {
      Dialog1Demo,
      Dialog2Demo,
    }
  },
}
</script>
