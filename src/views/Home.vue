<template>
  <div class="home-page">
    <div class="topnavAndBanner">
      <Topnav></Topnav>
      <div class="banner">
        <svg>
          <use xlink:href="#icon-pear"></use>
        </svg>
        <h1>梨 UI</h1>
        <h2>一个平平无奇，普普通通的 UI 框架</h2>
        <p class="actions">
          <a href="https://github.com/lilian-han/pear-ui">GitHub</a>
          <router-link to="/doc">开始</router-link>
        </p>
      </div>
    </div>
    <div class="footer">
      <div class="hr"></div>
      <div class="features">
        <ul>
          <li>
            <svg class="icon">
              <use xlink:href="#icon-vue"></use>
            </svg>
            <h3>基于 Vue 3</h3>
            <p>骄傲的使用了 Vue 3 Composition API</p>
          </li>
          <li>
            <svg class="icon">
              <use xlink:href="#icon-ts"></use>
            </svg>
            <h3>基于 TypeScript</h3>
            <p>源代码采用 TypeScript 书写</p>
          </li>
          <li>
            <svg class="icon">
              <use xlink:href="#icon-idea"></use>
            </svg>
            <h3>代码易读</h3>
            <p>每个组件的源代码都及其简洁</p>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Topnav from '../components/Topnav.vue'
export default {
  components: {
    Topnav,
  },
}
</script>

<style lang="scss" scoped>
$green: #02bcb0;
$border-radius: 4px;
$color: #007974;

.home-page {
  width: 100%;
}

.banner {
  color: $color;
  padding: 120px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  > svg {
    margin-bottom: 50px;
  }

  > .actions {
    padding: 8px 0;

    a {
      margin: 0 8px;
      background: $green;
      color: white;
      display: inline-block;
      padding: 8px 24px;
      border-radius: $border-radius;

      &:hover {
        text-decoration: none;
      }
    }
  }
}

.footer {
  margin: auto auto;
  width: 100%;

  @media (min-width: 800px) {
    width: calc(100% - 60px);
  }

  @media (min-width: 1200px) {
    width: calc(100% - 60px);
  }

  .hr {
    height: 5px;
    background: #b8eae7;
    margin-bottom: 5px;
  }

  .features {
    background: #b8eae7;
    width: 100%;
    height: 450px;

    > ul {
      > li {
        width: 100%;
      }
    }

    //
    @media (min-width: 1200px) {
      height: 260px;

      > ul {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        height: 260px;

        > li {
          width: 33.3333%;
        }
      }
    }

    > ul {
      > li {
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 150px;

        > svg {
          width: 104px;
          height: 104px;
          position: absolute;
          z-index: 1;
        }

        > h3 {
          font-size: 28px;
        }

        > h3,
        p {
          z-index: 2;
          display: block;
          margin: 10px 0;
        }
      }
    }
  }
}
</style>
