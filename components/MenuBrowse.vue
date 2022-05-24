<template>
  <div class="menuBrowse">
    <div class="menuItems">
      <button v-for="group in imageGroups"
              @click="filterOptions"
              v-bind:value="group.type" :key="group.type">
        {{ group.title2 }}
      </button>
    </div>
    <div class="pictureOptions">
      <div class="pictureDesc"
        v-for="group in imageGroups" :key="group.type"
        v-if="subKeyName == '' || subKeyName == group.type ">
          <div class="title">{{group.title}}</div>
          <div class="desc">{{group.desc}}</div>

          <div class="imageSection" >
            <imgDetail
              v-for="subOpt in group.subOptions"
              :key="subOpt.key"
              v-bind:keyNumber="subOpt.key"></imgDetail>
          </div>

      </div>
    </div>
  </div>

</template>
<script>
export default {
  data() {
    return {
      // List of available menu items.
      menuItems: Array(),
      // Image detail groups
      imageGroups: Object(),
      subKeyName:"",
    }
  },
  methods:{
    filterOptions: function (eventData){
      if (eventData instanceof Object){
        this.subKeyName = eventData.currentTarget.value
      }
    }
  },

  async fetch() {
    console.log("Menu Browse...")
    const data = await require(`~/assets/image_details.json`)
    const contentDesc = await require('~/assets/content_desc.json')
    if (contentDesc instanceof Array) {
      for (var contentKey in contentDesc) {
        var contentItem = contentDesc[contentKey]
        contentDesc[contentKey].subOptions = Array()
        // Loop around the image list - Map those items which
        //  match the key to there corresponding image list/reference
        //  point.
        for (var dataKey in data) {
          var dataItem = data[dataKey]
          if (dataItem.group == contentItem.type) {
            contentDesc[contentKey].subOptions.push(dataItem)
          }
        }
      }


      // Setup the rendering for the display of the content buttons
      this.imageGroups = contentDesc
    }
  }
}
</script>
