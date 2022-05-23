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
      title: "Sidmouth Town Photos",

      meta: [
        {
          "name": "description",
          "content": "Sidmouth Beach Photos"
        },
        {
          "name": "keywords",
          "content": "Sidmouth Town Photos Pictures of Sidmouth Guide Explore Beach Sea Defence Rocks"
        }
      ]
    }
  }
}
</script>
