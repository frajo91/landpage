<script setup>
import fecha from './components/fechahora.vue'
import TheWelcome from './components/clase.vue'
import videoplayer from './components/videoplayer.vue'
import { onMounted, onBeforeUnmount, onBeforeUpdate, onUpdated ,reactive, computed,ref,toRaw} from 'vue'
import axios from 'axios';
var datos=ref(null);

onMounted(async () => {
  const response = await axios.get("./json/videos.json")
  datos.value = toRaw(response.data)

})
const open = ref(false);
const titulo = ref(null);
const video = ref(null);
const showModal = (clase) => {
  open.value = true;
  titulo.value=clase.titulo;
  video.value=clase.video;
};

    const irAnterior=()=> {
      window.location.href = 'https://universidadsaluddigestiva.com/2024/';
    }

</script>

<template>
  <a-app>
    <a-config-provider
    :theme="{
      token: {
        fontFamily: 'Lato',
        colorPrimary:'#00b837ff',
        fontSize:16,
      },
    }"
  >
    <a-layout class="transparente">
       <a-space direction="vertical"   width="100%">
      <a-layout-content class="container1">
        <a-space direction="vertical"  width="100%">
          <a-row justify="center"  align="bottom">
            <img src="/imagen1.png" alt="" class="img-100">
            <a-col :xs="22" :md="18"><a-typography-paragraph style="text-align: center;">Es un programa de educación médica continuada, diseñado para profesionales de la salud interesados en mantenerse actualizados en patologías gastrointestinales.</a-typography-paragraph> </a-col>
          </a-row>
          <a-row justify="center" align="middle"> 
             <a-col :xs="7" :md="6">
              <a-row justify="center">
                <img src="/logo1.png" alt="" :width="70">
              </a-row>
              <a-row justify="center" >
                <a-typography-title class="text-big">12</a-typography-title>
              </a-row >
              <a-row justify="center">
                <a-typography-text>Sesiones de</a-typography-text>
              </a-row>
              <a-row justify="center">
                <a-typography-text>actualización</a-typography-text>
              </a-row>
            </a-col>
            <a-col >
              <img src="/divider.png" alt="" class="divider">
            </a-col>
             <a-col :xs="11" :md="6">
              <a-row justify="center">
                <img src="/logo1.png" alt="" :width="70">
              </a-row>
              <a-row justify="center" align="bottom">
                <a-typography-text>Todos los</a-typography-text>
              </a-row>
              <a-row justify="center" >
                <a-typography-title class="text-big">JUEVES</a-typography-title>
              </a-row >
              <a-row justify="center">
                <a-typography-text>Inicio 28 de agosto</a-typography-text>
              </a-row>
              </a-col>
            <a-col >
              <img src="/divider.png" alt="" class="divider">
            </a-col>
             <a-col :xs="5" :md="6">
              <a-row justify="center">
                <img src="/logo1.png" alt="" :width="70">
              </a-row>
              <a-row justify="center" >
                <a-typography-title class="text-big">1</a-typography-title>
              </a-row >
              <a-row justify="center">
                <a-typography-text>Hora por</a-typography-text>
              </a-row>
              <a-row justify="center">
                <a-typography-text>sesión</a-typography-text>
              </a-row>
            </a-col>
          </a-row>
          <a-row justify="center">
            <a-col :xs="22" :md="18" class="linea-difuminada">
            <a-typography-paragraph style="text-align: center; padding: 8px;">Durante estas sesiones, se abordarán las patologías gastrointestinales más frecuentes en la práctica clínica, brindando información actualizada, casos clínicos relevantes y discusiones interactivas.</a-typography-paragraph>
            </a-col>
          </a-row>
          <a-row justify="space-around" :gutter="16" align="middle">
            <a-col :xs="22" :md="12" >
              <videoplayer v-if="datos!=null" v-bind:url="datos.bienvenida.video"/>
               
            </a-col>
             <a-col :xs="22" :md="10" >
                <a-row justify="center" align="middle">
                  <a-col>
                    <a-row>
                      <a-typography-title :level="2" class="text-big" v-if="datos!=null" v-html="datos.bienvenida.titulo"></a-typography-title>
                    </a-row>
                    <a-row>
                      <a-typography-text v-if="datos!=null" v-html="datos.bienvenida.descripcion"></a-typography-text> 
                    </a-row>
                    <fecha  v-if="datos!=null" v-bind:fecha="datos.bienvenida.fecha"/>
                  </a-col>
                </a-row>
            </a-col>
          </a-row>
          <a-row justify="space-around" align="top" :gutter="[24,48]" style="padding: 24px; padding-bottom: 24px;">
            <a-col class="macroclase" :xs="22" :md="8" v-if="datos!=null" v-for="clase in toRaw(datos.clases)">
                <a-row  justify="start" class="row-h100" align="center">
                  <a-col   :span="24" class="linea-difuminada3">
                    <a-row justify="center" align="middle" class="clase linea-difuminada2" >
                      <a-space size="middle">
                      <img v-if="clase.video!=''" src="/play.png" alt="" class="play">
                      <img v-if="clase.video==''" src="/playno.png" alt="" class="play">
                      <a-typography-title :level="4" 
                        :class="{
                            'text-big': true,        // Siempre se aplica
                            'sin_video': clase.video=='',   // Solo si hay video
                          }">CLASE {{clase.id}}</a-typography-title>
                      </a-space>
                    </a-row>
                    <a-row justify="center" style="text-align: center;">
                      <a-typography-link @click="showModal(clase)"  
                      :class="{
                          'text-big2': true,        // Siempre se aplica
                          'm-0': true,             // Siempre se aplica
                          'sin_video': clase.video=='',   // Solo si hay video
                        }"  >{{clase.titulo}}</a-typography-link>
                    </a-row>
                    <a-row justify="center">
                      <a-typography-text  class="m-0" style="color: gray;text-align:center; ">{{clase.docente}}</a-typography-text>
                    </a-row>
                  </a-col>
          
                  <a-col :span="24" style="align-content: end; margin-top: 10px;">
                    <a-config-provider
                      :theme="{
                        token: {
                          fontFamily: 'Lato',
                          colorPrimary:'purple',
                          fontSize:12,
                        },
                      }"
                    >
                    <a-row justify="center" align="middle" :gutter="16" >
                      <a-col>
                        <a-row justify="end">
                          <a-typography-text class="m-0">{{clase.fecha.dia}}</a-typography-text>
                        </a-row>
                        <a-row justify="end">
                          <a-typography-title  
                          :class="{
                            'text-big': true,        // Siempre se aplica
                            'm-0': true,             // Siempre se aplica
                            'sin_video': clase.video=='',   // Solo si hay video
                          }">{{clase.fecha.dianumber}}</a-typography-title>
                        </a-row>
                        <a-row justify="end">
                          <a-typography-text class="m-0">{{clase.fecha.mes}}</a-typography-text>
                        </a-row>
                      </a-col>
                      <a-col>
                        <img src="/divider2.png" alt="" style="height: 60px">
                      </a-col>
                      <a-col class="col-center">
                        <a-row align="bottom">
                          <a-col><a-typography-title 
                             :class="{
                                'text-big': true,        // Siempre se aplica
                                'm-0': true,             // Siempre se aplica
                                'sin_video': clase.video=='',   // Solo si hay video
                              }">7:00</a-typography-title></a-col>
                          <a-col><a-typography-text>p.m.</a-typography-text> </a-col>
                        </a-row>
                      </a-col>
                    </a-row>
                    </a-config-provider>
                  </a-col>
                    
                </a-row>

     
              
            </a-col>
            <a-modal
                  v-model:open="open"
                  v-bind:title="titulo"
                  :footer="null"
                >
                <videoplayer v-bind:url="video"/>
                </a-modal>
          </a-row>
        </a-space>
      </a-layout-content>
      <a-row justify="center" class="transparente container1">
        <a-col>
          <a-button type="primary" shape="round" class="button_version" size="large" @click="irAnterior()">
            HAZ CLIC AQUÍ PARA VER LA VERSIÓN 1
          </a-button>
        </a-col>
        <a-col :xs="24">
          <a-row justify="space-around" :gutter="[16,16]" align="middle">
            <a-col :xs="8" :md="5"  >
              <img src="/footer1.png" alt="" style="height: auto;width: 100%; padding: 8px ;">
            </a-col>
            
            <a-col :xs="8" :md="5" >
              <img src="/footer2.png" alt="" style="height: auto;width: 100%; padding: 8px;">
            </a-col>
            
            <a-col :xs="8" :md="5" >
              <img src="/footer3.png" alt="" style="height: auto;width: 100%; padding: 8px;">
            </a-col>
            
            <a-col :xs="8" :md="5" >
              <img src="/footer4.png" alt="" style="height: auto;width: 100%; padding: 8px;">
            </a-col>
            
            <a-col :xs="8" :md="5" >
              <img src="/footer5.png" alt="" style="height: auto;width: 100%; padding: 8px;">
            </a-col>
            <a-col :xs="8" :md="5" >
              <img src="/footer6.png" alt="" style="height: auto;width: 100%; padding: 8px;">
            </a-col>
            <a-col :xs="8" :md="5" >
              <img src="/footer7.png" alt="" style="height: auto;width: 100%; padding: 8px;">
            </a-col>
          </a-row>
          
        </a-col>
        </a-row>
      
    </a-space>
    </a-layout>

      </a-config-provider>
</a-app>
<a-row style="background-color: white;text-align: center;width: 100vw;position: fixed;bottom: 0px;left: 0px ;" justify="center">
        <a-typography-text class="text-big">MATERIAL DIRIGIDO AL CUERPO MÉDICO</a-typography-text>
      </a-row>
  </template>

<style scoped>
a-app{
  width: 100%;
  height: 100%;
}

</style>
