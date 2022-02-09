<template>
  <div id="nav">
    {{$store.state.title}}
    <Notes />
    <!-- <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> -->
  </div>
  <!-- <router-view/> -->
</template>
<script>
import Notes from "./components/Notes.vue";
export default {
  name:"App",
  components:{
    Notes
  },
}
</script>
<style>
</style>
