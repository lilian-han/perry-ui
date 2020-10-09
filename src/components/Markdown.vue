<template>
  <articel class="markdown-body" v-html="content"></articel>
</template>

<script lang="ts">
export default {
  props: {
    content: {
      type: String,
      required: true,
    },
  },
}
</script>
