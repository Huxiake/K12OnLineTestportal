<template>
  <div class="dashboard-container">
    <div class="bg-image">111</div>
    <div class="welcome">111</div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  computed: {
    ...mapGetters([
      'name',
      'roles'
    ])
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.dashboard {
  &-container {
    margin: 0;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
.welcome {
  display: block;
  height: 900px;
}
.bg-image {
  background: url("../../assets/bg-img.jpg") no-repeat 50%;
  background-color: rgba(0, 0, 0, 0);
  height: 1280px;
}
</style>
