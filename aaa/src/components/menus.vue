<template>
  <div class="navMenu">
    <label v-for="navMenu in navMenus" :key="navMenu.path">
      <!--只有一级菜单-->
      <el-menu-item v-if="!navMenu.children" :index="navMenu.path" :route="navMenu.path">
        <!--图标-->
        <i :class="navMenu.icon"></i>
        <!--标题-->
        <span slot="title">{{navMenu.title}}</span>
      </el-menu-item>
      <!--有多级菜单-->
      <el-submenu v-if="navMenu.children" :key="navMenu.path" :index="navMenu.path">
        <template slot="title">
          <i :class="navMenu.icon"></i>
          <span> {{navMenu.title}}</span>
        </template>
        <!--递归组件，把遍历的值传回子组件，完成递归调用-->
        <nav-menu :navMenus="navMenu.children"></nav-menu>
      </el-submenu>
    </label>

  </div>
</template>

<script>
  export default {
    name: 'NavMenu', //使用递归组件必须要有
    props: ['navMenus'], // 传入子组件的数据
    data() {
      return {}
    },
    methods: {
      
    }
  }
</script>

<style scoped>

</style>