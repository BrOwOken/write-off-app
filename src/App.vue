<template>
  <div class="main">
    <h1 class="mb-3">Odpisová Kalkulačka</h1>
      <router-view v-slot="{ Component }">
        <transition name="router" mode="out-in">
          <component :is="Component"></component>
        </transition>
      </router-view>
  </div>
</template>

<script>
import WriteOff from "@/views/WriteOff";
export default {
  name: "App",
  components: {
    WriteOff
  }
}
</script>

<style lang="scss">
#app {
  //font-family: 'Poppins', sans-serif;
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
.router{
  &-enter-active, &-leave-active{
    transition: all 0.5s cubic-bezier(.21,.81,.7,.91);
  }
  &-enter-from{
    transform: translateX(-48px);
    opacity: 0;
  }
  &-leave-to{
    transform: translateX(48px);
    opacity: 0;
  }
}
@media screen and(max-width: 600px){
  .main{
    margin: 48px 32px;
  }
}
</style>
