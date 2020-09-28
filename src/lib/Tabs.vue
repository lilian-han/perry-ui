<template>
<div class="aha-tabs">
  <div class="aha-tabs-nav" ref="container">
    <div class="aha-tabs-nav-item" :ref="
          (el) => {
            if (el) navItems[index] = el
          }
        " @click="select(t)" :class="{ selected: t === selected }" v-for="(t, index) in titles" :key="index">
      {{ t }}
    </div>
    <div class="aha-tabs-nav-indicator" ref="indicator"></div>
  </div>
  <div class="aha-tabs-content">
    <component class="aha-tabs-content-item" :is="current" :key="current.props.title" />
  </div>
</div>
</template>

<script lang="ts">
import {
  computed,
  onMounted,
  onUpdated,
  ref
} from 'vue'
import Tab from './Tab.vue'
export default {
  props: {
    selected: {
      type: String,
    },
  },
  setup(props, context) {
    const navItems = ref < HTMLDivElement[] > ([])
    const indicator = ref < HTMLDivElement > (null)
    const container = ref < HTMLDivElement > (null)
    const x = () => {
      const divs = navItems.value
      const result = divs.filter((div) => div.classList.contains('selected'))[0]
      const {
        width
      } = result.getBoundingClientRect()
      indicator.value.style.width = width + 'px'
      const {
        left: left1
      } = container.value.getBoundingClientRect()
      const {
        left: left2
      } = result.getBoundingClientRect()
      const left = left2 - left1
      indicator.value.style.left = left + 'px'
    }
    onMounted(x)
    onUpdated(x)
    const defaults = context.slots.default()
    defaults.forEach((tag) => {
      if (tag.type !== Tab) {
        throw new Error('Tabs 子标签必须是 Tab')
      }
    })
    const titles = defaults.map((tag) => {
      return tag.props.title
    })
    const current = computed(() => {
      return defaults.filter((tag) => {
        return tag.props.title === props.selected
      })[0]
    })
    const select = (title: String) => {
      context.emit('update:selected', title)
    }
    return {
      navItems,
      container,
      indicator,
      defaults,
      titles,
      current,
      select,
    }
  },
}
</script>

<style lang="scss">
$blue: #40a9ff;
$color: #333;
$border-color: #d9d9d9;

.aha-tabs {
  &-nav {
    display: flex;
    color: $color;
    border-bottom: 1px solid $border-color;
    position: relative;

    &-item {
      padding: 8px 0;
      margin: 0 16px;
      cursor: pointer;

      &:first-child {
        margin-left: 0;
      }

      &.selected {
        color: $blue;
      }
    }

    &-indicator {
      position: absolute;
      height: 3px;
      background: $blue;
      left: 0;
      bottom: -1px;
      width: 100px;
      border-radius: 1.5px;
      transition: 0.25s;
    }
  }

  &-content {
    padding: 8px 0;
  }
}
</style>
