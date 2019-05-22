<template>
  <div class="big-header">
    <h1>{{ message }}</h1>
    <br />
    <router-link class="button" to="/page">Go to Page</router-link>
    <br />
    <button class="button" @click="handleClick">Click me up</button>
    <link rel="preload">
  </div>
</template>
 
 <style scoped>
 
 </style>
 
<script>
import countService from '../services/countService';
import game from '../data.json'; 


export default {
  data() {
    return {
      message: 'Hello Hetic'
    };
  },
  methods: {
    handleClick() {
      countService.increment();
    }
  }
};

</script>
