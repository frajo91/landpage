<script setup>
import fecha from './fechahora2.vue'
import videoplayer from './videoplayer.vue'
import { toRaw,ref } from 'vue';
defineProps({
  clase:{
    type:Object,
    required:true
  }
});

const open = ref(false);
const showModal = () => {
  open.value = true;
};



</script>

<template>
  <a-col :xs="22" :md="7">
    <a-row class="clase" justify="center" align="middle" >
        <a-typography-text class="m-0" style="color: white !important">CLASE {{clase.id}}</a-typography-text>
        <img v-if="clase.video!=''" src="/play.png" alt="" class="play">
    </a-row>
    <a-row  justify="center" align="middle" >
      <a-col :span="24" style="text-align: center;"><a-typography-link @click="showModal" class="m-0 text-big" >{{clase.titulo}}</a-typography-link></a-col>
      <a-col><a-typography-text  class="m-0" style="color: gray;">{{clase.docente}}</a-typography-text></a-col>
    </a-row>
    <a-config-provider
    :theme="{
      token: {
        fontFamily: 'Lato',
        colorPrimary:'purple',
        fontSize:12,
      },
    }"
  >
    <a-row justify="center" align="middle" :gutter="16" style="padding:10px;">
    <a-col>
      <a-row justify="end">
        <a-typography-text class="m-0">JUEVES</a-typography-text>
      </a-row>
      <a-row justify="end">
        <a-typography-title class="text-big m-0">{{clase.fecha.dianumber}}</a-typography-title>
      </a-row>
      <a-row justify="end">
        <a-typography-text class="m-0">{{clase.fecha.mes}}</a-typography-text>
      </a-row>
    </a-col>
    <a-col>
      <img src="/divider2.png" alt="" style="height: 90%">
    </a-col>
    <a-col class="col-center">
      <a-row align="bottom">
        <a-col><a-typography-title class="text-big m-0">7:00</a-typography-title></a-col>
        <a-col><a-typography-text>p.m.</a-typography-text> </a-col>
      </a-row>
    </a-col>
  </a-row>
  </a-config-provider>
  </a-col>
  <a-modal
      v-model:open="open"
      v-bind:title="clase.titulo"
      :footer="null"
    >
    <videoplayer v-bind:url="clase.video"/>
    </a-modal>
</template>
