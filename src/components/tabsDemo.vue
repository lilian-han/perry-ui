<template>
<div>Tabs 示例</div>
<h1>示例1</h1>
<Tabs v-model:selected="selected">
  <Tab title="导航1">我是 tab1</Tab>
  <Tab title="导航2222222">内容 tab2</Tab>
</Tabs>
</template>

<script lang="ts">
import Tabs from '../lib/Tabs.vue'
import Tab from '../lib/Tab.vue'
import {
  ref
} from 'vue'
export default {
  components: {
    Tabs,
    Tab,
  },
  setup() {
    const selected = ref('导航1')
    return {
      selected,
    }
  },
}
</script>
