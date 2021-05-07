<template>
  <div class="main">
    <h1>Odpisová Kalkulačka</h1>
    <router-view/>
  </div>
</template>

<style lang="scss">
#app {
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #181717;
}
body{
  margin: 0;
}
.main{
  margin: 96px 72px;
  display: flex;
  justify-content: center;
  flex-flow: column;
}
</style>
