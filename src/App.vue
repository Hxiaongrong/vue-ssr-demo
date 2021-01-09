<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
@Component({})
export default class App extends Vue {
  mounted() {
    const t = performance.timing;
    console.log('DNS解析耗时:', t.domainLookupEnd - t.domainLookupStart);
    console.log('TCP连接耗时:', t.connectEnd - t.connectStart);
    console.log('SSL安全连接耗时:', t.connectEnd - t.secureConnectionStart);
    console.log('网络请求耗时(TTFB):', t.responseStart - t.requestStart);
    console.log('数据传输耗时:', t.responseEnd - t.responseStart);
    console.log('DOM解析耗时:', t.domInteractive - t.responseEnd);
    console.log('资源加载耗时:', t.loadEventStart - t.domContentLoadedEventEnd);
    console.log('首包时间:', t.responseStart - t.domainLookupStart);
    console.log('首次渲染时间 / 白屏时间:', t.responseEnd - t.fetchStart);
    console.log('首次可交互时间:', t.domInteractive - t.fetchStart);
    console.log('DOM Ready时间:', t.domContentLoadedEventEnd - t.fetchStart);
    console.log('页面完全加载时间:', t.loadEventStart - t.fetchStart);
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
