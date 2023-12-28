<script>
import Nav from "@/components/Nav.vue";
import {defineComponent} from "vue";

export default defineComponent({
  components: {Nav}
})

</script>

<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>
