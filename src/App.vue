<template>
  <MainView />
</template>

<style lang="scss">
#app {
  color: #2c3e50;
}
body {
  margin: 0;
  padding: 0;
}
</style>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import MainView from "@/views/MainView.vue"; // @ is an alias to /src

@Options({
  components: {
    MainView,
  },
})
export default class App extends Vue {}
</script>