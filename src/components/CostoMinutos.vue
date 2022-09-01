<template>
  <h1>Calcular costo llamada</h1>

  <p>Cuánto duró su llamada? (En minutos)</p>

  <input type="number" v-model="minutos"/>
   
  <button @click="calcular" id="A" class="boton">Calcular</button>
    
  <div>
    <textarea readonly id="area" cols="30" rows="4" placeholder="Esperando orden..."></textarea>
  </div>

</template>


<script>
export default {
  name: 'CostoMinutos',
  prop:{
    title: {
      type: Text,
      default: 'CostoMinutos'
    }
  },
  data(){
    return{
      minutos: null
    }
  },
  methods: {
    calcular(){
      let losMinutos = Math.ceil(this.minutos);
      let costo;
      let res = 'El total a pagar por '+ this.minutos + ' minutos, es: ';
          
      if(losMinutos <= 3){
        costo = 100;
      }
      else{
        costo = 100 + (losMinutos-3)*50
      }
      document.getElementById('area').innerHTML = res + costo;

      this.minutos = null;
    }
  }
}

</script>

<style scoped>
  textarea{
    resize: none;
  }
</style>