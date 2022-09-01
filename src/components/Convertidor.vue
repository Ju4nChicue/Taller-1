<template>
    
    <h1> {{title}} </h1>
    
    <input type="number" v-model="segundos"/>
   
    <button @click="convertir" id="A" class="boton">Convertir</button>
    
    <div>
        <textarea readonly id="area" cols="30" rows="4" placeholder="Esperando orden..."></textarea>
    </div>
    
</template>


<script>
    export default{
        props: {
            title: {
                type: String,
                default: 'Convertidor de segundos a hh:mm:ss'
            }
        },
        name: 'Convertidor',
        data(){
                return{
                    segundos: 6340,
                    items: []
                }
            }
        ,methods:{
            convertir(){
                let losSegundos = this.segundos%60;
                let losMinutos = ~~(this.segundos/60)%60;
                let lasHoras = ~~((~~(this.segundos/60))/60);

                document.getElementById('area').innerHTML = this.segundos + ' segundos, son: ' + lasHoras + ' Hora/s, ' +
                        losMinutos + ' minutos y ' + losSegundos + ' segundos.';

                this.segundos = null;

            }
        }
    }
</script>

<style scoped>
    h1{
        color: aquamarine;
        font-size:x-large;
    }
    span{
        color: red;
        font-size: 20px;
    }

    button{
        width:80px;
        height:19px;
        font-weight:bold;
        background-color: cornflowerblue;
        cursor: pointer;
    }
    #A:hover{
        background-color:rgb(44, 203, 203);
    }
    
    #area{
        position: relative;
        top: 20px;
        resize: none;
    }
</style>