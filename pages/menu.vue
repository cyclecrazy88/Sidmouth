<template>
  <client-only>
    <div>
      <heading hideOptions="1" />
      <MenuBrowse/>
    </div>

  </client-only>
</template>

<script>
import MenuBrowse from '../components/MenuBrowse.vue'
export default {
    name: "IndexPage",
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
        };
    },
    components: { MenuBrowse }
}
</script>
