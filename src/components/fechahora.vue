<script setup>
defineProps({
  dia: {
    type: String,
    required: true
  },
  dianumber: {
    type: String,
    required: true
  },
  mes: {
    type: String,
    required: true
  },
  hora: {
    type: String,
    required: true
  },
  ampm: {
    type: String,
    required: true
  }
})
</script>

<template>
  <a-row justify="center" :gutter="16">
    <a-col>
      <a-row justify="end">
        <a-typography-title :level="3" class="m-0">{{dia}}</a-typography-title>
      </a-row>
      <a-row justify="end">
        <a-typography-title class="text-big m-0">{{dianumber}}</a-typography-title>
      </a-row>
      <a-row justify="end">
        <a-typography-title :level="3" class="m-0">{{mes}}</a-typography-title>
      </a-row>
    </a-col>
    <a-col>
      <img src="/divider2.png" alt="">
    </a-col>
    <a-col class="col-center">
      <a-row align="bottom">
        <a-col><a-typography-title class="text-big m-0">{{hora}}</a-typography-title></a-col>
        <a-col><a-typography-text>{{ampm}}</a-typography-text> </a-col>
      </a-row>
    </a-col>
  </a-row>
</template>

<style scoped>
</style>
