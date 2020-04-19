<template>
  <div>
    <el-menu
      ref="menu"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      :collapse="isCollapse"
    >
      <template v-for="(item,index) of list">
        <el-submenu :index="index+''" v-if="item.children" :key="index" :style="{paddingLeft:(item.level-1)*20+'px'}" >
          <template slot="title">
            <i :class="item.icon"></i>
            <span>{{item.title}}</span>
          </template>
          <menu-list @select="select" :list="item.children"></menu-list>
          <!--递归调用-->
        </el-submenu>
        <el-menu-item  @click="select(item)" :index="index+''" v-else :key="index" :style="{paddingLeft:item.level*20+'px'}">
          <i :class="item.icon"></i>
          <span slot="title">{{item.title}}</span>
        </el-menu-item>
      </template>
    </el-menu>
  </div>
  <!-- <li role="menuitem" tabindex="-1" class="el-menu-item" style="padding-left: 40px;">选项2</li> -->
</template>
<script>
export default {
  name: "MenuList",
  props: {
    list: Array,
    isCollapse: Boolean
  },
  data() {
    return {
    };
  },
  computed: {
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
    select(e){
      this.$emit('select',e);
    }
  }
};
</script>
<style>
</style>
