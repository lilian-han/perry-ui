<demo>
支持 disabled
</demo>
<template>
  <Switch v-model:value="bool" disabled />
</template>

<script lang="ts">
import { ref } from 'vue'
import { Switch } from 'perry-ui'
export default {
  components: {
    Switch,
  },
  setup() {
    const bool = ref(false)
    return {
      bool,
    }
  },
}
</script>
