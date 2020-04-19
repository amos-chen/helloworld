<template>
  <div>
    <b-navbar type="dark" style="background:#008DFF">
      <b-navbar-nav>
        <b-nav-item-dropdown :text="application" left>
          <b-dropdown-item
            v-for="(item,index) in applications"
            :key="index"
            @click="applicationClick(item)"
            href="#"
          >{{item}}</b-dropdown-item>
        </b-nav-item-dropdown>
        <b-navbar-nav class="ml-auto rightNav" style="align-items:center;">
          <a href="#" style="color:#FFFFFF;padding:0 20px;">
            <i class="el-icon-search" @click="openSearch"></i>
          </a>
          <a href="#" style="color:#FFFFFF;" v-b-toggle.sidebar-right>
            <b-icon-grid-fill @click="sideMenuOpen"></b-icon-grid-fill>
          </a>
        </b-navbar-nav>
      </b-navbar-nav>
    </b-navbar>
    <b-sidebar id="sidebar-right" no-header right shadow v-model="visible" bg-variant="light">
      <div class="sideBarContent" style="hieght:100%;margin-top:15px;">
        <el-row style="margin:0 auto;">
          <span style="font-size:24px;">å¼€æ”¾å¹³å�°</span>
        </el-row>
        <el-row>
            <side-menu @select="select"></side-menu>
        </el-row>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
import SideMenu from './SideMenu';
export default {
  name: "mobile-header",
  components:{
      SideMenu
  },
  data() {
    return {
      application: "",
      hide: undefined,
      visible: false
    };
  },
  props: {
    applications: Array,
    bodyClick: Number
  },
  watch: {
    bodyClick() {
      this.hideSideBar();
    }
  },
  beforeMount() {
    this.application = this.applications[0];
  },
  methods: {
    applicationClick(item) {
      this.application = item;
    },
    sideMenuOpen() {},
    openSearch() {},
    hideSideBar() {
      this.visible = false;
    },
    select(e){
        this.$emit('select',e);
    }
  }
};
</script>

<style>
.rightNav {
  position: absolute;
  right: 15px;
  height: 56px;
  top: 0;
}
#sidebar-right {
  background: white !important;
}
.sideBarContent{
    display: flex;
    flex-direction: column;
    /* align-items: center; */
}
</style>
