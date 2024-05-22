<script setup>
defineProps({
  url: {
    type: String,
    required: true
  }
})
</script>

<template>
  <a-row justify="center" align="middle" class="video">
    <a-typography-text v-if="url==''" style="color: white;">Disponible proximamente
          </a-typography-text> 
     <video  v-bind:src="url" class="player" controls></video>
  </a-row>
</template>

<style scoped>

</style>
