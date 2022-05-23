<template>
  <client-only>
    <div>
      <heading />
      <imageMenu />
    </div>

  </client-only>
</template>

<script>
export default {
  name: 'IndexPage',

  head() {
    return {
      title: "SidFord Photos",

      meta: [
        {
          "name": "description",
          "content": "SidFord Photos"
        },
        {
          "name": "keywords",
          "content": "Sidmouth Town Photos Pictures of SidFord Guide Explore"
        }
      ]
    }
  }
}
</script>
