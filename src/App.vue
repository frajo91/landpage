<script setup>
import fecha from './components/fechahora.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <a-app>
    <a-config-provider
    :theme="{
      token: {
        fontFamily: 'Lato',
        colorPrimary:'purple',
        fontSize:16,
      },
    }"
  >
    <a-layout class="transparente">
       <a-space direction="vertical" :size="large" :align="center" width="100%">
      <a-layout-content class="container1">
        <a-space direction="vertical" :size="large" :align="center" width="100%">
          <a-row justify="center"  align="bottom">
            <img src="/imagen1.png" alt="" class="img-100">
            <a-col :xs="22" :md="18"><a-typography-paragraph style="text-align: center;">Es un programa de educación medica continuada, diseñado para profesionales de la salud interesados en mantenerse actualizados en patologías gastrointestinales.</a-typography-paragraph> </a-col>
          </a-row>
          <a-row justify="center" align="middle"> 
             <a-col :xs="7" :md="6">
              <a-row justify="center">
                <img src="/logo1.png" alt="" :width="50">
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
                <img src="/logo1.png" alt="" :width="50">
              </a-row>
              <a-row justify="center" align="bottom">
                <a-typography-text>Todos los</a-typography-text>
              </a-row>
              <a-row justify="center" >
                <a-typography-title class="text-big">JUEVES</a-typography-title>
              </a-row >
              <a-row justify="center">
                <a-typography-text>Inicio 30 de mayo</a-typography-text>
              </a-row>
              </a-col>
            <a-col >
              <img src="/divider.png" alt="" class="divider">
            </a-col>
             <a-col :xs="5" :md="6">
              <a-row justify="center">
                <img src="/logo1.png" alt="" :width="50">
              </a-row>
              <a-row justify="center" >
                <a-typography-title class="text-big">1</a-typography-title>
              </a-row >
              <a-row justify="center">
                <a-typography-text>Hora por</a-typography-text>
              </a-row>
              <a-row justify="center">
                <a-typography-text>sección</a-typography-text>
              </a-row>
            </a-col>
          </a-row>
          <a-row justify="center">
            <a-col :xs="22" :md="18">
            <a-typography-paragraph style="text-align: center; padding: 8px;" >Durante estas sesiones, se abordarán las patologías gastrointestinales más frecuentes en la práctica clínica, brindando información actualizada, casos clínicos relevantes y discusiones interactivas.</a-typography-paragraph>
            </a-col>
          </a-row>
          <a-row justify="space-around" align="middle">
            <a-col :xs="22" :md="10" >
              <a-row justify="center" align="middle" class="video">
                 <video src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" class="player" controls></video>
              </a-row>
               
            </a-col>
             <a-col :xs="22" :md="8" >
                <a-row justify="center" align="middle">
                  <a-col>
                    <a-row>
                      <a-typography-title class="text-big">BIENVENIDA AL CURSO</a-typography-title>
                    </a-row>
                    <a-row>
                      <a-typography-text>Universidad Procaps® y Médicos de la
                        Fundación Santa Fe y miembros activos de la
                        sociedad de Gastroenterología Colombiana
                      </a-typography-text> 
                    </a-row>
                    <fecha  dia="JUEVES" dianumber="30" mes="MAYO" hora="7:00" ampm="p.m." />
                  </a-col>
                </a-row>
            </a-col>
          </a-row>
          <a-row>
            <TheWelcome/>
          </a-row>
        </a-space>
      </a-layout-content>
      <a-layout-footer class="transparente">Footer</a-layout-footer>
    </a-space>
    </a-layout>
      </a-config-provider>
</a-app>
</template>

<style scoped>
a-app{
  width: 100%;
  height: 100%;
}

</style>
