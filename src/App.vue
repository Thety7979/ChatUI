<template>
  <div>
    <ChatUI />
  </div>
</template>

<script>
import ChatUI from './components/ChatUI.vue'
export default {
  name: 'App',
  components: {
    ChatUI
  }
}
</script>

<style>
body {
  font-family: 'Roboto', sans-serif;
}
</style>