<template>
  <div class="item">
    <h4 style="color:#2995FE">{{title}}</h4>
    <p class="content">{{content}}</p>
    <hr>
  </div>
</template>

<script>
export default {
    name:"search-item",
    props:{
        title:String,
        content:String
    }
}
</script>

<style>
.item{
    display: flex;
    flex-direction: column;
}
</style>
