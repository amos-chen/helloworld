<template>
  <div>
    <el-menu
      background-color="#008DFF"
      text-color="#FFFFFF"
      :default-active="activeIndex"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
    >
      <el-row style="height:100%" align="middle" justify="center">
        <el-col :span="5">
          <div style="display:flex;align-items:center;height:100%;">
            <a href="#" :style="logoStyle">
              <el-image
                fit="contain"
                :src="require('../assets/img/logo.png')"
                style="padding:0 5px 0 15px;border-right:2px solid #ffffff;"
              ></el-image>
              <div style="padding-left:5px">开放平台</div>
            </a>
          </div>
        </el-col>
        <el-col :span="3">
          <el-submenu index="1" background-color="#FFFFFF">
            <template slot="title">{{application}}</template>
            <el-menu-item
              @click="applicationClick(item)"
              :index="'1-'+(index+1)"
              v-for="(item,index) in subMenu"
              :key="index"
            >{{item}}</el-menu-item>
          </el-submenu>
        </el-col>
        <el-col :span="2">
          <el-menu-item index="2" style="color:#FFFFFF">快速入门</el-menu-item>
        </el-col>
        <el-col :span="2">
          <el-menu-item index="3" style="color:#FFFFFF">服务的API</el-menu-item>
        </el-col>
        <el-col :span="2">
          <el-menu-item index="4" style="color:#FFFFFF">客户端API</el-menu-item>
        </el-col>
        <el-col :span="1">
          <el-menu-item index="5" style="color:#FFFFFF">组件</el-menu-item>
        </el-col>
        <el-col :span="2">
          <el-menu-item index="6" style="color:#FFFFFF">工具与资源</el-menu-item>
        </el-col>
        <el-col :span="1">
          <el-menu-item index="6" style="color:#FFFFFF">附录</el-menu-item>
        </el-col>
        <el-col :span="2">
          <el-menu-item index="6" style="color:#FFFFFF">技术支持</el-menu-item>
        </el-col>
        <el-col :span="3">
            <!-- <a href="#" v-show="!showSearchInput" @click="showSearch">
              <i class="el-icon-search" style="color:#FFFFFF;"></i>
            </a> -->
            <!-- <div v-show="showSearchInput"> -->
              <el-input
                ref="searchBar"
                placeholder="请输入内容"
                prefix-icon="el-icon-search"
                v-model="searchContent"
                @blur="hideSearchBar"
              />
            <!-- </div> -->
        </el-col>
      </el-row>
    </el-menu>
  </div>
</template>

<script>
export default {
    name:"header",
  data() {
    return {
      activeIndex: "1",
      application: "",
      subMenu: ["企业内部应用", "第三方企业应用"],
      logoStyle: {
        display: "flex",
        flexDirection: "row",
        fontSize: "24px",
        alignItems: "center",
        color: "#FFFFFF",
        textDecoration: "none",
        height: "32px",
        lineHeight: "32px"
      },
      showSearchInput: false,
      searchContent: ""
    };
  },
  beforeMount() {
    this.application = this.subMenu[0];
  },
  methods: {
    applicationClick(item) {
      this.application = item;
    },
    handleSelect(e) {
      console.log(e);
    },
    showSearch() {
      this.showSearchInput = !this.showSearchInput;
      this.$nextTick(() => {
        this.$refs.searchBar.focus();
      });
    },
    hideSearchBar() {
      if (!this.searchContent) {
        this.showSearchInput = false;
      }
    },
    isMobile(){
        let flag = navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i);
        return flag;
    }
  }
};
</script>

<style>
.el-menu--popup .el-menu-item {
  background-color: #ffffff !important;
  color: black !important;
}
.el-menu--popup .el-menu-item:hover {
  background-color: #e6f7ff !important;
}
.el-menu--popup {
  background-color: #ffffff !important;
}
.el-submenu__title i {
  color: #ffffff !important;
}
.el-submenu__title {
  color: #ffffff !important;
}
.el-submenu__title:hover {
  background-color: #008dff !important;
}
.el-menu-item:hover {
  background-color: #008dff !important;
}
.el-menu-item {
  padding: 0 10px !important;
}
.el-col {
  height: 56px;
  line-height: 56px;
}
</style>
