<template>
  <el-container>
    <el-header>
      <Header />
    </el-header>
    <el-container>
      <el-aside width="200px">
        <Aside />
      </el-aside>
      <el-container class="container-main">
        <el-main>
          <router-view :key="Date.now()" />
        </el-main>
        <el-footer>
          <Footer />
        </el-footer>
      </el-container>
    </el-container>
  </el-container>
  <router-link to="/">Home</router-link>
  <router-link to="/document/1">About</router-link>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Header from "@/components/Header.vue"; // @ is an alias to /src
import Aside from "@/components/Aside.vue"; // @ is an alias to /src
import Footer from "@/components/Footer.vue"; // @ is an alias to /src

@Options({
  components: {
    Header,
    Aside,
    Footer,
  },
})
export default class MainView extends Vue {}
</script>

<style scoped>
.container-main {
  background-color: #eee;
}
.el-header {
  display: flex;
  align-items: center;
}
</style>