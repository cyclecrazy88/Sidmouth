<template>
  <div class="imageMenu">
    <div class="imgTitle">{{menuTitle}}</div>
    <div class="imgDesc">{{menuDesc}}</div>

    <div class="imageSection">
      <imgDetail v-for="(imgItem,imgKey) in displayList"
        v-bind:key="imgItem.key"
        v-bind:keyNumber="imgItem.key"/>
    </div>
  </div>
</template>
<script>
export default {

  data(){
    return {
      displayList:Array(),
      menuDesc:"",
      menuTitle:"",
    }
  },

  async fetch(){
    //console.log("Image Menu...");
    // Get display information for the page - control configuration how to load
    //  the page etc.
    const data = await require(`~/assets/image_details.json`)
    const contentDesc = await require('~/assets/content_desc.json')

    // Get the search details, search parms etc.
    const searchOption = new URLSearchParams(window.location.search).get("type")

    for (var contentKey in contentDesc){
      var contentItem = contentDesc[contentKey]
      if (contentItem.type == searchOption){
        this.menuDesc = contentItem.desc
        this.menuTitle = contentItem.title
        break;
      }
    }

    // Loop around find detail display information for the page.
    const resultList = Array();
    if (typeof searchOption == "string")
    if (data instanceof Array){
      for (var dataKey in data){
        var dataItem = data[dataKey]
        if (dataItem.group == searchOption){
          resultList.push(dataItem)
        }
      }
    }
    this.displayList = resultList
  }
}
</script>
