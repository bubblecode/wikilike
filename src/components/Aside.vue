<template>
  <div class="aside">
    Aside
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  components: {
  },
})
export default class Aside extends Vue {}
</script>

<style lang="scss">
.el-aside {
  background-color: #fff;
  border-radius: 0px 8px 8px 0px;
  box-shadow: 0px 0px 3px 3px #ccc;
  z-index: 1;
}
.aside {
  height: 90%;
}
</style>