<template>
  <div>
    <nuxt-link to="/jokes">Back To Jokes</nuxt-link>
    <hr>
    <small>Joke ID: {{ $route.params.id }}</small>
  </div>
</template>

<script>
// import axios from "axios";
export default {

}  
</script>

<style>
</style>