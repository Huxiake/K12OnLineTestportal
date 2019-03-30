<template>
  <div class="navbar">
    <!-- <hamburger :toggle-click="toggleSideBar" :is-active="sidebar.opened" class="hamburger-container"/> -->
    <!-- <breadcrumb /> -->
    <!-- <el-dropdown class="avatar-container" trigger="click">
      <div class="avatar-wrapper">
        <img :src="avatar+'?imageView2/1/w/80/h/80'" class="user-avatar">
        <i class="el-icon-caret-bottom"/>
      </div>
      <el-dropdown-menu slot="dropdown" class="user-dropdown">
        <router-link class="inlineBlock" to="/">
          <el-dropdown-item>
            首页
          </el-dropdown-item>
        </router-link>
        <router-link class="inlineBlock" to="/">
          <el-dropdown-item>
            个人中心
          </el-dropdown-item>
        </router-link>
        <el-dropdown-item divided>
          <span style="display:block;" @click="logout">退出</span>
        </el-dropdown-item>
      </el-dropdown-menu>
    </el-dropdown> -->
    <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
      <el-menu-item index="1">首页</el-menu-item>
      <el-menu-item index="2" >产品</el-menu-item>
      <el-menu-item index="2" >服务报价</el-menu-item>
      <el-menu-item index="2" >帮助中心</el-menu-item>
      <el-menu-item index="2" >联系方式</el-menu-item>
      <el-button class="login-btn" type="primary" size="big" round>立即登录</el-button>
    </el-menu>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Breadcrumb from '@/components/Breadcrumb'
import Hamburger from '@/components/Hamburger'

export default {
  components: {
    Breadcrumb,
    Hamburger
  },
  data() {
    return {
      activeIndex: '1'
    }
  },
  computed: {
    ...mapGetters([
      'sidebar',
      'avatar'
    ])
  },
  methods: {
    toggleSideBar() {
      this.$store.dispatch('ToggleSideBar')
    },
    logout() {
      this.$store.dispatch('LogOut').then(() => {
        location.reload() // 为了重新实例化vue-router对象 避免bug
      })
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.navbar {
  position: fixed;
  width: 100%;
  height: 70px;
  padding: 0 20%;
  line-height: 70px;
  background-color: #FFFFFF;
  box-shadow: 0 1px 3px 0 rgba(0,0,0,.12), 0 0 3px 0 rgba(0,0,0,.04);
  z-index: 9999;
  .hamburger-container {
    line-height: 58px;
    height: 50px;
    float: left;
    padding: 0 10px;
  }
  .screenfull {
    position: absolute;
    right: 90px;
    top: 16px;
    color: red;
  }
  .avatar-container {
    height: 50px;
    display: inline-block;
    position: absolute;
    right: 35px;
    .avatar-wrapper {
      cursor: pointer;
      margin-top: 5px;
      position: relative;
      line-height: initial;
      .user-avatar {
        width: 40px;
        height: 40px;
        border-radius: 10px;
      }
      .el-icon-caret-bottom {
        position: absolute;
        right: -20px;
        top: 25px;
        font-size: 12px;
      }
    }
  }
  .login-btn {
    float: right;
    margin-left: 50px;
    margin-top: 6px;
  }
}
</style>

<style lang="scss">
.el-menu {
  padding: 15px auto;
  margin-top: 9px;
}
.el-menu--horizontal > .el-menu-item {
  margin-left: 3%;
}
.el-menu.el-menu--horizontal {
  border-bottom: solid 0px #e6e6e6;
}
.el-menu--horizontal > .el-menu-item.is-active {
  border-bottom: 3px solid #4A9;
}
</style>

