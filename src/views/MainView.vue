<template>
  <el-container>
    <el-header>
      <Header />
    </el-header>
    <el-container>
      <el-aside width="200px">
        <Aside />
      </el-aside>
      <el-container>
        <el-main>
          <Content />
        </el-main>
        <el-footer>
          <Footer />
        </el-footer>
      </el-container>
    </el-container>
  </el-container>
  <!-- <router-link to="/about">About</router-link> -->
  <router-view />
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Header from "@/components/Header.vue"; // @ is an alias to /src
import Aside from "@/components/Aside.vue"; // @ is an alias to /src
import Footer from "@/components/Footer.vue"; // @ is an alias to /src
import Content from "@/components/Content.vue";


@Options({
  components: {
    Header,
    Aside,
    Footer,
    Content,
  },
})
export default class MainView extends Vue {}
</script>
