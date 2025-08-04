<script setup>
defineProps({
  url: {
    type: String,
    required: true
  }
})

window.addEventListener('contextmenu', function (e) { 
  // do something here... 
  e.preventDefault(); 
}, false);

</script>

<template>
  <a-row justify="center" align="middle" class="video" >
    <a-typography-text v-if="url==''" style="color: white;">Disponible proximamente
          </a-typography-text> 
     <video @click.right="none" @contextmenu="false"  v-if="url!=''" class="player" controls controlslist="nodownload">
       <source :src="url" type="video/mp4" />
         Tu navegador no soporta la reproducción de video.
     </video>
  </a-row>
</template>

<style scoped>

</style>
