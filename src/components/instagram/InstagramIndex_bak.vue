<template>
  <el-container>
    <el-aside style="width: 200px;margin-top: 20px">
      <switch></switch>
      <SideMenu></SideMenu>
    </el-aside>
    <el-main>
      <books class="ins-area"></books>
    </el-main>
  </el-container>
</template>

<script>
import SideMenu from './InsSideMenu'
import Books from '../library/Books'
export default {
  name: 'AppInstagram',
  components: {SideMenu, Books}
}
</script>

<style scoped>
.ins-area {
  width: 990px;
  margin-left: auto;
  margin-right: auto;
}
</style>
