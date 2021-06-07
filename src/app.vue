<template>
  <div id="app">
    <header class="header-main">
      <span id="logo">Template Vue Component</span>
    </header>
    <div class="app-main">
      <router-view />
    </div>
  </div>
</template>

<style lang="less">
body {
  margin: 0;
  padding: 75px 0 0;
}

html,
body,
button,
input {
  font-size: 14px;
  color: #333;
  font-family: 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', '微软雅黑', Arial, sans-serif;
}

.header-main {
  background-color: #fff;
  color: #158dff;
  padding: 16px 50px;
  font-size: 24px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  z-index: 99;
}

.app-main {
  padding: 16px 30px;
}

</style>
