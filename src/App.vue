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

/*const datos={
   "bienvenida":{
         "titulo":"BIENVENIDA AL CURSO",
         "descripcion": "Universidad Procaps® y Médicos de la Fundación Santa Fe y miembros activos de la sociedad de Gastroenterología Colombiana",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"30",
            "mes":"MAYO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":"http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
   },
   "clases":[
      {
         "id":1,
         "titulo":"DISPEPSIA FUNCIONAL",
         "docente":"DR. FERNANDO SIERRA",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"06",
            "mes":"JUNIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":"http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
      },
      {
         "id":2,
         "titulo":"ABORDAJE INTEGRAL DEL DOLOR OBDOMINAL AGUDO Y CRÓNICO",
         "docente":"DR. REYNALDO RINCÓN",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"13",
            "mes":"JUNIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":"http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
      },
      {
         "id":3,
         "titulo":"SII UNA REALIDAD DOLOROSA Y MOLESTA",
         "docente":"DR. FABIAN JULIAO",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"20",
            "mes":"JUNIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":4,
         "titulo":"REFLUJO GASTROESOFÁGICO, LO QUE EL MÉDICO DEBE SABER",
         "docente":"DR. FERNANDO PINEDA",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"27",
            "mes":"JUNIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":5,
         "titulo":"ABORDAJE INTEGRAL DEL PACIENTE CON DIARREA CRÓNICA",
         "docente":"DR. FABIAN JULIAO",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"04",
            "mes":"JULIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":6,
         "titulo":"ULCERA PÉPTICA E INFECCIÓN POR HELICOBACTER PYLORI ¿EN QUE ESTAMOS?",
         "docente":"DR. FERNANDO SIERRA",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"11",
            "mes":"JULIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":7,
         "titulo":"ENFOQUE INTEGRAL DEL ESTREÑIMIENTO CRÓNICO",
         "docente":"DR. REYNALDO RINCÓN",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"18",
            "mes":"JULIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":8,
         "titulo":"SII ASOCIADO A SOBRECRECIMIENTO BACTERIANO - SIBO",
         "docente":"DR. VIVIANA OBANDO",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"25",
            "mes":"JULIO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":9,
         "titulo":"ENFERMEDAD HEPÁTICA GRASA NO ALCOHÓLICA",
         "docente":"DR. FERNANDO SIERRA",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"01",
            "mes":"AGOSTO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":10,
         "titulo":"MANEJO ACTUAL DEL VÓMITO Y NÁUSEAS, Y ASPECTOS CLÍNICO TERAPÉUTICOS",
         "docente":"DR. FERNANDO PINEDA",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"08",
            "mes":"AGOSTO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":11,
         "titulo":"TRANSAMINITIS",
         "docente":"DR. FERNANDO SIERRA",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"15",
            "mes":"AGOSTO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      },
      {
         "id":12,
         "titulo":"PROBIÓTICOS Y SALUD GASTROINTESTINAL",
         "docente":"DR. VIVIANA OBANDO",
         "fecha":{
            "dia":"JUEVES",
            "dianumber":"22",
            "mes":"AGOSTO",
            "hora":"7:00",
            "ampm":"p.m."
         },
         "video":""
      }

   ]
};*/


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
       <a-space direction="vertical"   width="100%">
      <a-layout-content class="container1">
        <a-space direction="vertical"  width="100%">
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
              <videoplayer v-if="datos!=null" v-bind:url="datos.bienvenida.video"/>
               
            </a-col>
             <a-col :xs="22" :md="8" >
                <a-row justify="center" align="middle">
                  <a-col>
                    <a-row>
                      <a-typography-title class="text-big" v-if="datos!=null">{{datos.bienvenida.titulo}}</a-typography-title>
                    </a-row>
                    <a-row>
                      <a-typography-text v-if="datos!=null">{{datos.bienvenida.descripcion}}
                      </a-typography-text> 
                    </a-row>
                    <fecha  v-if="datos!=null" v-bind:fecha="datos.bienvenida.fecha"/>
                  </a-col>
                </a-row>
            </a-col>
          </a-row>
          <a-row justify="space-around" align="top" :gutter="[16,16]" style="padding: 16px;">
            <a-col :xs="22" :md="7" v-if="datos!=null" v-for="clase in toRaw(datos.clases)">
                <a-row class="clase" justify="center" align="middle" >
                    <a-typography-text class="m-0" style="color: white !important">CLASE {{clase.id}}</a-typography-text>
                    <img v-if="clase.video!=''" src="/play.png" alt="" class="play">
                </a-row>
                <a-row  justify="center" align="middle" >
                  <a-col :span="24" style="text-align: center;"><a-typography-link @click="showModal(clase)" class="m-0 text-big" >{{clase.titulo}}</a-typography-link></a-col>
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
                  v-bind:title="titulo"
                  :footer="null"
                >
                <videoplayer v-bind:url="video"/>
                </a-modal>
          </a-row>
        </a-space>
      </a-layout-content>
      <a-row justify="center" class="transparente">
        <a-col :xs="24" :md="20" >
          <img src="/footer.png" alt="" style="height: auto;width: 100%;">
        </a-col>
        <a-col :xs="24" :md="20" >
          <a-config-provider
            :theme="{
              token: {
                fontFamily: 'Lato',
                colorPrimary:'purple',
                fontSize:8,
              },
            }"
          >
          <a-typography-paragraph style="color: white;">
            EZOLIUM®: Esomeprazol magnésico tri hidrato 44,5 mg equivalente a esomeprazol base 40.00000 mg. 1ndicaciones: Reﬂujo gastroesofág ico (rge), (tratamiento de la esofagits por reﬂujo erosivo, tratamiento preventvo a largo plazo de recaídas de esofagits cicatrizada, tratamiento Sintomátco del reﬂujo gastroesofágico), en combinación con 
            un régimen terapéutco, Antbacteriano adecuado para erradicar helicobacter pylori y para: cicatrización de la Ulcera duodenal asociada con helicobacter pylori; prevención de recaídas de úlceras Péptcas en los pacientes con úlceras relacionadas con helicobacter pylori. Tratamiento del síndrome de zollinger-ellison. CONTRAINDICA CIONES. Hiper-
            sensibilidad conocida al esomeprazol, a los benzimidazoles susttuidos o a cualquier otro componente de la fórmula. REGISTRO SANITARIO: INVIMA 2019M-0015016-R1. PRODUO®: COMPOSICIÓN: Cada cápsula blanda contene Bromuro de Pinaverio100 mg; Simetcona331,492 mg equivalentea Dimetcona 300 mg.INDICACIONES:Antes-
            pasmódico y antﬂatulento. CONTRAINDICACIONES: Hipersensibilidad al principio actvo o alguno de los excipientes, embarazo y lactancia. PRESENTACIÓN: Caja x 32 CBG capsulas de liberación no modiﬁcada oral capsula 1,0000u. REGISTRO SANITARIO: 2022 M-0020736. MENTSII®: COMPOSICIÓN: Cada cápsula gastro-resistente contene 
            aceite de menta (mentha x piperita l.) 187.00000 mg. INDICACIONES: Alivio sintomátco de trastornos digestvos como la dispepsia y la ﬂatulencia. Antespasmódico y carminatvo. CONTRAINDICACIONES: hipersensibilidad a los componentes de la planta. Embarazo y lactancia. Niños menores de 4 años. PRESENTACIÓN: Caja x 30 cápsulas blan-
            das de gelatna. REGISTRO SANITARIO PFT2022-0002844. MUVETT®: Reg. San. INVIMA 2003M-0002555 Muvet ﬂora: Reg. San. INVIMA 2001 M-0000192 Muvet: Reg. San. INVIMA 2002M-00001363 Muvet S 60U: Reg. San. INVIMA 2004M-0003716 Muvet S 21U: Reg. San. INVIMA 2004M-0003716. IFAXIM®: Reg. San. INVIMA 
            2016M- 0017375
          </a-typography-paragraph>
        </a-config-provider>
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
