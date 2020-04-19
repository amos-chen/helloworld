<template>
  <div>
    <div class="header">
      <pc-header @pcSearch="pcSearch" @pcSearchClear="pcSearchClear" :applications="applications" v-if="!isMobile"></pc-header>
      <mobile-header @select="select" :bodyClick="bodyClick" :applications="applications" v-if="isMobile"></mobile-header>
    </div>
    <div class="container-fluid" @click="clickBody">
      <el-row>
        <el-col :span="5" class="bd-sidebar border-bottom-0">
          <nav id="bd-docs-nav" aria-label="Main navigation" class="bd-links d-none d-md-block">
            <side-menu @select="select"></side-menu>
          </nav>
        </el-col>
        <el-col :span="19" class="bd-content pl-md-3">
          <div class="bd-links d-md-block" v-if="!isPcSearch">
            <div v-if="!isMobile" v-html="html" style="max-width:1920px;"></div>
            <div v-if="isMobile" v-html="html" style="max-width:768px;"></div>
          </div>
          <div class="bd-links" v-else style="margin:0 10px;">
            <search-item v-for="(item,index) in searchContents" :key="index" :title="item.title" :content="item.content"></search-item>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
// import Header from "../components/Header";
import PcHeader from "../components/PcHeader";
import MobileHeader from "../components/MobileHeader";
import SideMenu from "../components/SideMenu";
import SearchItem from "../components/SearchItem";
export default {
  components: {
    // Header,
    PcHeader,
    SideMenu,
    MobileHeader,
    SearchItem
  },
  data() {
    return {
      isPcSearch:false,
      applications: ["企业内部应用", "第三方企业应用"],
      searchContents:[
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."},
        {title:'产品上架流程',content:"应用上架市场安全<em>测试</em>报告指南<em>测试</em>并填写《安全<em>测试</em>报告结果.docx》并转成PDF格式进行提交，报告最终内容可参考《某某应用安全<em>测试</em>报告结果(样例).pdf》常见问题截图时，请将工具的完整界面全部截下来(包含请求内容、返回内容)，不要进行压缩直接附在报告里。问:报告需要提供哪些信息，是否每个用例都要<em>测试</em>?答:报告里..."}
      ],
      isMobile:true,
      bodyClick:1,
      change:true,
      html: '',
      html1:'<h1>Trix</h1>'+
'<div>Trix is an open-source project from&nbsp;<a href="https://basecamp.com/">Basecamp</a>, the creators of Ruby on Rails. Millions of people trust their text to Basecamp, and we built Trix to give them the best possible editing experience.</div>'+
'<div class="attachment-gallery attachment-gallery--2">'+
'<figure class="attachment attachment--preview attachment--png" contenteditable="false" data-trix-attachment="{&quot;contentType&quot;:&quot;image/png&quot;,&quot;filename&quot;:&quot;plan-01.png&quot;,&quot;filesize&quot;:56843,&quot;height&quot;:700,&quot;url&quot;:&quot;/images/attachments/plan-01.png&quot;,&quot;width&quot;:800}" data-trix-content-type="image/png" data-trix-id="53" data-trix-attributes="{&quot;presentation&quot;:&quot;gallery&quot;}"><img src="https://trix-editor.org/images/attachments/plan-01.png" width="800" height="700" data-trix-mutable="true" data-trix-store-key="imageElement/53/https://trix-editor.org/images/attachments/plan-01.png/337/295" />'+
'<figcaption class="attachment__caption" data-trix-placeholder="Add a caption&hellip;"></figcaption>'+
'</figure>'+
'<figure class="attachment attachment--preview attachment--png" contenteditable="false" data-trix-attachment="{&quot;contentType&quot;:&quot;image/png&quot;,&quot;filename&quot;:&quot;plan-02.png&quot;,&quot;filesize&quot;:62054,&quot;height&quot;:700,&quot;url&quot;:&quot;/images/attachments/plan-02.png&quot;,&quot;width&quot;:800}" data-trix-content-type="image/png" data-trix-id="58" data-trix-attributes="{&quot;presentation&quot;:&quot;gallery&quot;}"><img src="https://trix-editor.org/images/attachments/plan-02.png" width="800" height="700" data-trix-mutable="true" data-trix-store-key="imageElement/58/https://trix-editor.org/images/attachments/plan-02.png/337/295" />'+
'<figcaption class="attachment__caption" data-trix-placeholder="Add a caption&hellip;"></figcaption>'+
'</figure>'+
'</div>'+
'<div>&nbsp;</div>'+
'<h1>Different By Design</h1>'+
'<div>Most WYSIWYG editors are wrappers around HTML&rsquo;s contenteditable and execCommand APIs, designed by Microsoft to support live editing of web pages in Internet Explorer 5.5, and eventually reverse-engineered and copied by other browsers.</div>'+
'<div>&nbsp;</div>'+
'<div>Because these APIs were never fully specified or documented, and because WYSIWYG HTML editors are enormous in scope, each browser&rsquo;s implementation has its own set of bugs and quirks, and JavaScript developers are left to resolve the inconsistencies.</div>'+
'<div>'+
'<figure class="attachment attachment--preview attachment--png" contenteditable="false" data-trix-attachment="{&quot;contentType&quot;:&quot;image/png&quot;,&quot;filename&quot;:&quot;rained-on.png&quot;,&quot;filesize&quot;:44180,&quot;height&quot;:500,&quot;url&quot;:&quot;/images/attachments/rained-on.png&quot;,&quot;width&quot;:1500}" data-trix-content-type="image/png" data-trix-id="143" data-trix-attributes="{&quot;presentation&quot;:&quot;gallery&quot;}"><img src="https://trix-editor.org/images/attachments/rained-on.png" width="1500" height="500" data-trix-mutable="true" data-trix-store-key="imageElement/143/https://trix-editor.org/images/attachments/rained-on.png/712/237" />'+
'<figcaption class="attachment__caption" data-trix-placeholder="Add a caption&hellip;"></figcaption>'+
'</figure>'+
'</div>'+
'<div>Trix sidesteps these inconsistencies by treating contenteditable as an I/O device: when input makes its way to the editor, Trix converts that input into an editing operation on its internal document model, then re-renders that document back into the editor. This gives Trix complete control over what happens after every keystroke, and avoids the need to use execCommand at all.</div>'+
'<div>&nbsp;</div>'+
'<div><strong>Trix was created by</strong></div>'+
'<ul>'+
'<li>Sam Stephenson (<a href="https://twitter.com/sstephenson">@sstephenson</a>)</li>'+
'<li>Javan Makhmali (<a href="https://twitter.com/javan">@javan</a>)</li>'+
'</ul>'+
'<div>&nbsp;</div>'+
'<div><em>Thanks for checking it out!</em></div>',
      html2:'<h1>Hello world</h1>'
    };
  },
  beforeMount() {
    this.isMobile = this.isMobileFunc();
    this.html = this.html2;
  },
  methods: {
    clickBody(){
      this.bodyClick += 1;
    },
    isMobileFunc(){
        let flag = navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i);
        return flag;
    },
    select(){
      if(this.change){
        this.html = this.html1;
      }else{
        this.html = this.html2;
      }
      this.change = !this.change;
    },
    pcSearch(searchContent){
      this.isPcSearch = true;
      console.log(searchContent);
    },
    pcSearchClear(){
      this.isPcSearch = false;
    }
  }
};
</script>

<style>
.header{
  width: 100%;
  position: sticky;
  z-index: 1000;
}
@media (min-width: 768px){
  .bd-links{
      max-height: calc(100vh - 4rem);
      overflow: auto;
  }
  .bd-content{
    padding-right: 0!important;
  }
}
.bd-links{
  padding-top: 1rem;
}
.container-fluid{
  padding-right: 0!important;
}
.container-fluid img{
  max-width: 100%;
}

</style>
