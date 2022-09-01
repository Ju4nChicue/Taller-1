<template>
  
  <h1>Saludo</h1>

  <input type="text" v-model="currentName"/>
  <input type="time" v-model="currentTime"/>

  <button @click="newMessage" id="A" class="boton">Saludar</button>

  <p>{{answer}}</p>
  
</template>


<script>
export default {
  name: 'Saludo',
  props:{
    title: ''
  },
  data(){
    return{
      currentName: null,
      currentTime: null,
      answer: ''
    }
  },
  methods: {
    newMessage(){
      
      if(this.currentName == null){
        this.answer = 'Ingrese un nombre, por favor';
      }

      else{
        if(this.currentTime >= '06:00' && this.currentTime <= '11:59'){
        this.answer = 'Buenos días, ' + this.currentName;
        }
        else if(this.currentTime >= '12:00' && this.currentTime <= '18:59'){
          this.answer = 'Buenos tardes, ' + this.currentName;
        }
        else{
          this.answer = 'Buenos noches, ' + this.currentName;
        }

        this.currentName = null;
        }
    }
  }
}
</script>


<style scoped>

  h1{
    color: skyblue;
  }
  input{
    border-radius: 4px;
  }

  button{
    background-color: gray;
    color: white;
  }
  button:hover{
    background-color: khaki;
    color: black;
    cursor: pointer;
  }
</style>