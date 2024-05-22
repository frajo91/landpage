<script setup>
defineProps({
  fecha:{
    type:Object,
    required:true
  }
})
</script>

<template>
  <a-row justify="center" align="middle" :gutter="16" style="padding:10px;">
    <a-col>
      <a-row justify="end">
        <a-typography-text class="m-0">{{fecha.dia}}</a-typography-text>
      </a-row>
      <a-row justify="end">
        <a-typography-title class="text-big m-0">{{fecha.dianumber}}</a-typography-title>
      </a-row>
      <a-row justify="end">
        <a-typography-text class="m-0">{{fecha.mes}}</a-typography-text>
      </a-row>
    </a-col>
    <a-col>
      <img src="/divider2.png" alt="" style="height: 90%">
    </a-col>
    <a-col class="col-center">
      <a-row align="bottom">
        <a-col><a-typography-title class="text-big m-0">{{fecha.hora}}</a-typography-title></a-col>
        <a-col><a-typography-text>{{fecha.ampm}}</a-typography-text> </a-col>
      </a-row>
    </a-col>
  </a-row>
</template>

<style scoped>
</style>
