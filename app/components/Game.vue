<template>
  <div class="container" 
  rel="preload" 
  v-bind:style="{ 'background-img': 'url('+ step.img +')' }"
  >
    <h1>{{ step.title }}</h1>
    <ul>
      <li v-on:click="doActions(action)" v-for="action in step.actions" :key="action.step">
        <div>
          {{ action.label }}
        </div>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.container{
      background-size: 100%;
}
  .container {
    height: 100vh;
    background-repeat: no-repeat;
    

  }
</style>

<script>

import game from '../data.json';

export default {
  data: function() {
    return {
      step: game.steps.find(step => {
        return step.id === parseInt(this.$route.params.id)
      })
    }
  },
  mounted: function() {
    console.log()
  },
  watch: {
    '$route.params.id'(to, from) {
      this.step = this.getStep()
    }
  },
  methods: {
    getStep() {
      return game.steps.find(step => {
        return step.id === parseInt(this.$route.params.id)
      })
    },
    doActions(action) {
      if (action.to) {
        this.$router.push({params: {id: action.to}})
      }
      if (action.lose === 'Game Over') {
        localStorage.setItem('endGame', action.reason)
        this.$router.push({path: '/lose'})
      }
    }
  }
}

</script>
