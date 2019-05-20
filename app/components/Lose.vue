<template>
  <div>{{ messageLose }}</div>
</template>

<script>
export default {
  data() {
    return {
      messageLose: localStorage.getItem('endGame')
    }
  }
};
</script>
