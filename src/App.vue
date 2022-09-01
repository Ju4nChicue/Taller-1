<template>
  <body>
    <button @click="cambioMenos">Anterior</button>
    <button @click="cambioMas">Siguiente</button>

    <Convertidor v-if="pagina==1"/>
    <CostoMinutos v-if="pagina==2"/>
    <Saludo v-if="pagina==3"/>
    <Iguales v-if="pagina==4"/>
    <ListaOrdenada v-if="pagina==5"/>
    <Impares v-if="pagina==6"/>
    <Salarios v-if="pagina==7"/>
    <Indice v-if="pagina==8"/>
    <Tabla v-if="pagina==9"/>
    <!--<Suma_Matriz v-if="pagina==10"/> PENDIENTE-->
    <Alumno v-if="pagina==11"/>
    <Objeto_Alumno v-if="pagina==12"/>
  </body>
  
</template>

<script>
  import Convertidor from '@/components/Convertidor.vue';
  import CostoMinutos from '@/components/CostoMinutos.vue';
  import Saludo from '@/components/Saludo_3.vue';
  import Iguales from '@/components/Iguales_4.vue';
  import ListaOrdenada from '@/components/Lista_5.vue';
  import Impares from '@/components/Impares_6.vue';
  import Salarios from '@/components/Salarios_7.vue';
  import Indice from '@/components/Indice_8.vue';
  import Tabla from '@/components/Tabla_9.vue';
  import Suma_Matriz from '@/components/Suma_Matriz_10.vue';
  import Alumno from '@/components/Alumno_11.vue';
  import Objeto_Alumno from '@/components/Objeto_Alumno_12.vue';

  export default {
    name: 'App',
    components: {
    Convertidor,
    CostoMinutos,
    Saludo,
    Iguales,
    ListaOrdenada,
    Impares,
    Salarios,
    Indice,
    Tabla,
    Suma_Matriz,
    Alumno,
    Objeto_Alumno

    },
    data(){
      return{
        pagina: 1
      }
    },
    methods: {
      cambioMas(){
        if(this.pagina<12){
          this.pagina ++;
        }
      },
      cambioMenos(){
        if(this.pagina>1){
          this.pagina --;
      }
    }
  }
  }


</script>

