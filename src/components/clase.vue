<script setup>
import fecha from './fechahora.vue'
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
    <fecha v-bind:fecha="toRaw(clase.fecha)" />
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
