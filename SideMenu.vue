<template>
  <div>
    <menu-list @select="select" :list="menuData" :isCollapse="isCollapse"></menu-list>
  </div>
</template>

<script>
import MenuList from "../components/MenuList";
export default {
  name: "side-menu",
  components: {
    MenuList
  },
  data() {
    return {
      isCollapse: false,
      menuData: [
        { title: "开发前必读", children: null,level:1 },
        { title: "概述", children: null,level:1 },
        {
          title: "We码小程序",
          children: [
            { title: "创建We码小程序", children: null,level:2 },
            { title: "We码小程序开发", children: null,level:2 }
          ],level:1
        },
        {
          title: "身份验证",
          children: [
            { title: "概述", children: null,level:2 },
            {
              title: "企业内部We码小程序免登",
              children: [
                { title: "概述", children: null,level:3 },
                { title: "错误码", children: null,level:3 }
              ]
              ,level:2
            }
          ]
          ,level:1
        }
      ]
    };
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
