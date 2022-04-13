<template>
  <div id="app">
    <NavigationComp />
    <router-view :key="$route.path" />
  </div>
</template>

<script>
import NavigationComp from "@/components/NavigationComp";
export default {
  components: { NavigationComp },
};
</script>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
}
* {
  margin: 0;
}

html,
body {
  height: 100%;
}
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}

img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
}
input,
button,
textarea,
select {
  font: inherit;
  outline: none;
  border: none;
}
p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
}
#app {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  padding: 0 10px;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
