<template>
  <div id="app">
    <header>
      <span>{{header_text}}</span>
    </header>
    <main>
      <router-view></router-view>
    </main>
    <footer>
      <span>{{footer_text}}</span>
    </footer>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      header_text: "#Nature",
      footer_text: "Beautiful Pictures"
    };
  }
};
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: center;
  margin-top: 40px;
}

header {
  margin: 0;
  height: 56px;
  padding: 0 16px 0 24px;
  background-color: #35495e;
  color: #ffffff;
}

header span {
  display: block;
  position: relative;
  font-size: 20px;
  line-height: 1;
  letter-spacing: 0.02em;
  font-weight: 400;
  box-sizing: border-box;
  padding-top: 16px;
}

footer {
  margin-top: 10px;
  height: 32px;
  background-color: #35495e;
  color: #ffffff;
  position: absolute;
  bottom: 0;
  width: 100%;
  display: block;
}

footer span {
  display: block;
  position: relative;
  font-size: 12px;
  line-height: 32px;
  letter-spacing: 0.02em;
  font-weight: 400;
  box-sizing: border-box;
  text-align: center;
}
</style>
