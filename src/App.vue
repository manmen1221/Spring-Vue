<template>
  <el-container>
    <el-header height="100px">
      <img src="./assets/head.png" height="100%">
    </el-header>
    <el-main>
      <router-view/>
    </el-main>
    <el-footer>
      2017011301
    </el-footer>
  </el-container>
</template>

<script>
export default {
  name: 'App'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .white-space {
    white-space:pre
  }
</style>
