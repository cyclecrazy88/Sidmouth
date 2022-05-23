<template>
  <div class="imageDetails">
    <div class="image_heading">{{heading}}</div>
    <div class="imageItem">
      <img v-bind:src="imgRef" class="imageItem" />
    </div>

    <div class="image_desc">{{desc}}</div>
  </div>
</template>
<script>
export default {
  props: ["keyNumber"],
  data() {
    return {
      "key": 0,
      "imgRef": null,
      "heading":"",
      "desc":"",
    }
  },

  async fetch() {
    console.log("Load Content...");

    var data = await require(`~/assets/image_details.json`);
    // Image content details
    var keyNumber = parseInt(this.keyNumber);
    var dataSource = "";
    if (data instanceof Object) {
      // Loop around the keys - Load/Initialize the key
      //  number item for the event data
      for (var dataKey in data) {
        var dataItem = data[dataKey]

        if (keyNumber == dataItem.key) {
          this.key = dataItem.key
          dataSource = dataItem.src
          // Render the source with the help of reqire from WebPack
          var source = require(`~/assets/images/${dataSource}`)
          this.imgRef = source
          this.heading = dataItem.heading;
          this.desc = dataItem.desc
          break;
        }
      }
    }
    return data;
  }
}
</script>
