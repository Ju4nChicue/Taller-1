<template>
    <body>
        <h1>Alumno</h1>

        <span v-if="info.length == 0">Nombre Estudiante: </span><input type="text" v-model="name" v-if="info.length == 0" />

        <div id="cuadro">
        <span>Nota Materia: </span><input id="nota" type="number" min="0" max="5" v-model="nota" />
        <button @click="addNota">Añadir</button>
        <button @click="deleteAll">Borrar Todo</button>
        </div>

        <h2 class="alerta" v-if="(name == null ||nota == null) && (info.length < 3)">Llene todos los campos, por favor</h2>
        <h2 class="alerta" v-if="nota != null && (nota < 1 || nota > 5)">Ingrese una nota ente 1 y 5 incluyendolos</h2>

        <h2 class="alerta" v-if="info.length < 3">Despues de ingresar 3 notas, se mostrará el resultado</h2>

        <p v-if="info.length == 3">Alumno {{name}}, {{answer}}</p>


    </body>
</template>

<script>
export default {
   name: 'Alumno',
   data(){
    return{
        name:null,
        nota: null,
        info: [],
        answer:''
    }
   },
   methods:{
    addNota(){
            if(this.name != null && this.nota != null){

                if(this.info.length<3 && this.nota>0 && this.nota<=5){
                  
                    this.info.push(this.nota);
                    this.nota = null;
                    }

                    if(this.info.length == 3){
                    let n = 0;
                    for(let i=0; i < this.info.length; i++){
                        n += this.info[i];
                    }

                    n = n/this.info.length;

                    if(n >= 3){
                        this.answer = 'su definitiva es: ' + n.toFixed(1) + ' APROBADO';
                    }
                    else{
                        this.answer = 'su definitiva es: ' + n.toFixed(1) + ' REPROBADO'
                    }
                }
                }
                
            },
            deleteAll(){
                this.info = [];
            }
    }
   }
</script>


<style scoped>
    h1{
        color: darkorchid;
        font-family: 'Lucida Sans';
    }
    input{
        border-radius: 5px;
    }
    span{
        color: azure;
        font-family: Cambria;
    }
    #cuadro{
        top: 20px;
    }

    .alerta{
        top: 40px;
    }
    #nota{
        width: 40px;
    }
    ul{
        top: 30px;
        background-color: black;
        width:fit-content;
    }
    li{
        color: antiquewhite;
    }
    p{
        top: 25px;
        color: burlywood;
        font-family: fantasy;
    }
    button:hover{
        cursor: pointer;
    }
    button{
        background-color: black;
        color: whitesmoke;
        border-color: whitesmoke;
    }
</style>