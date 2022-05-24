<template>
  <nav class="heading">
    <span>
      <NuxtLink to="/">Sidmouth Town Photos</NuxtLink>
    </span>
    <div class="linkButtons" v-if="hideOptions != '1'">
      <NuxtLink @click="buttonClick" to="beach?type=beach">Beach</NuxtLink>
      <NuxtLink @click="buttonClick" to="town?type=town">Town</NuxtLink>
      <NuxtLink @click="buttonClick" to="sidford?type=sidford">Sidford</NuxtLink>
      <NuxtLink @click="buttonClick" to="woolbrook?type=woolbrook">Woolbrook</NuxtLink>
      <NuxtLink @click="buttonClick" to="fortescue?type=fortescue">Fortescue</NuxtLink>
    </div>
    <div class="mobileMenu" v-if="hideOptions != '1'">
      <NuxtLink @click="buttonClick" to="menu">Local Photos</NuxtLink>
    </div>

  </nav>


</template>
<script>
export default {
  props:["hideOptions"],
  methods:{
    buttonClick:function(eventData){
      if (eventData instanceof Object){

      }
      console.log("Button Click")
    }
  }

  // new URLSearchParams(window.location.search).get("type")
}
</script>
