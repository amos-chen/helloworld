<template>
  <div>
    <b-navbar toggleable="lg" type="dark" style="background-color:#008DFF">
      <b-navbar-brand href="#">
        <img
          src="../assets/img/logo.png"
          class="d-inline-block align-top"
          alt="Kitten"
          style="padding:0 5px 0 15px;border-right:2px solid #ffffff;"
        />
        <span style="font-size:24px;padding-left:5px;">开放平台</span>
      </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item-dropdown :text="application" right>
            <b-dropdown-item
              style="padding:0 2px;"
              v-for="(item,index) in applications"
              :key="index"
              @click="applicationClick(item)"
            >{{item}}</b-dropdown-item>
          </b-nav-item-dropdown>
          <div
            @click="topLinkClick(index)"
            v-for="(item,index) in topMenu"
            :key="index"
            v-bind:class="{box_container_active:(clickItem===index&&dropdownShow),box_container:clickItem!==index}"
          >
            <b-nav-item href="#">{{item}}</b-nav-item>
          </div>
        </b-navbar-nav>
        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <!-- <b-nav-form> -->
            <el-input @change="submit" clearable @clear="clearInput" v-model="searchContent" size="sm" class="mr-sm-0" placeholder="Search"></el-input>
          <!-- </b-nav-form> -->
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "pc-header",
  data() {
    return {
      searchContent:'',
      application: "",
      topMenu: [
        "快速开始",
        "服务的API",
        "前端API",
        "组件",
        "工具与资源",
        "附录",
        "技术支持"
      ],
      clickItem: -1,
      dropdownShow: true
    };
  },
  props:{
    applications:Array,
  },
  beforeMount() {
    this.application = this.applications[0];
  },
  methods: {
    applicationClick(item) {
      this.application = item;
    },
    topLinkClick(index) {
      this.clickItem = index;
    },
    dropdown(event) {
      console.log(event);
    },
    submit(){
      if(this.searchContent){
        this.$emit("pcSearch",this.searchContent);
      }
    },
    clearInput(){
      this.$emit('pcSearchClear');
    }
  }
};
</script>

<style>
.dropdown-item:active {
  background-color: #ffffff !important;
  color: black !important;
}
.dropdown-item:hover {
  background-color: #e6f7ff !important;
}
.navbar-dark .navbar-nav .nav-link {
  color: #ffffff !important;
}
.navbar-dark .navbar-nav .nav-link:hover {
  background-color: rgba(255, 255, 255, 0.1) !important;
}
.navbar-collapse.collapse.show .navbar-nav .box_container_active::after {
  background: none !important;
}
@media (min-width: 992px) {
  .box_container::after {
    content: "";
    display: block;
    /* background: #FFFFFF; */
    width: 40%;
    height: 2px;
    margin: 0 auto;
  }
  .box_container_active::after {
    content: "";
    display: block;
    background: #ffffff;
    width: 40%;
    height: 2px;
    margin: 0 auto;
  }
}

.navbar-expand-lg .navbar-nav .nav-link {
  padding-left: 0.8rem !important;
  padding-right: 0.8rem !important;
}
</style>
