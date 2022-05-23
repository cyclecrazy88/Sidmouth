<template>
  <client-only>
    <div>
      <heading />
      <home />
    </div>

  </client-only>
</template>

<script>
export default {
  name: 'IndexPage',

  head() {
    return {
      title: "Sidmouth Town Photos",

      meta: [
        {
          "name": "description",
          "content": "Sidmouth Town Photos"
        },
        {
          "name": "keywords",
          "content": "Sidmouth Town Photos Pictures of Sidmouth Guide Explore"
        }
      ]
    }
  }
}
</script>
