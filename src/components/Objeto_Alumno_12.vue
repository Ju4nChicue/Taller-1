<template>
    <body>
        <h1>Guardar Alumno</h1>

        <p>Nombre Estudiante: </p><input type="text" v-model="name" />
        <button @click="addCourse">Añadir</button>
        <button @click="generarReporte">Reporte</button>

        <div id="contenedor">
            
            <div class="cuadro">
                <span>Nota1: </span><input id="nota" type="number" min="0" max="5" v-model="nota1" />
            </div>
    
            <div class="cuadro">
                <span>Nota2: </span><input id="nota" type="number" min="0" max="5" v-model="nota2" />
            </div>

            <div class="cuadro">
                <span>Nota3: </span><input id="nota" type="number" min="0" max="5" v-model="nota3" />
            </div>

        </div>

        
        <div class="area">
            <textarea readonly id="area" v-if="reporte" >{{reporte}}</textarea>
        </div>

        <h2 class="alerta">Si no llena todos los campos o si no ingresa notas entre 1 y 5 inclutendolos, no se ingresará</h2>

    </body>
</template>

<script>
export default {
   name: 'Alumno',
   data(){
    return{
        name:null,
        nota1: null,
        nota2: null,
        nota3: null,
        todos: [],
        reporte: ''
    }
   },
    methods:{
        addCourse(){
            if(this.name != null || this.nota1 != null || this.nota2 != null || this.nota3 != null){
                if(this.todos.length<3 && this.nota1>0 && this.nota1<=5 && this.nota2>0 && this.nota2<=5 && this.nota3>0 && this.nota3<=5){

                    let alumno = {nombre: this.name, 
                                n1: this.nota1,
                                n2: this.nota2,
                                n3: this.nota3,
                                definitiva: (this.nota1 + this.nota2 + this.nota3)/3,
                                res: ''
                                };
                                

                    if(alumno.definitiva>=3){
                        alumno.res = 'APROBADO';
                    }
                    else{
                        alumno.res = 'REPROBADO';
                    }
                    this.todos.push(alumno)

                    this.name = null;
                    this.nota1 = null;
                    this.nota2 = null;
                    this.nota3 = null;

                    console.log(this.todos)
                    }
                }
        },
        generarReporte(){
            this.reporte = '';
            for(let i = 0; i < this.todos.length; i++){
                this.reporte += 'Alumno: ' + this.todos[i].nombre + 
                '\n\nNotas:\n' + 
                'Nota 1: ' + this.todos[i].n1.toFixed(1) + '\n' +
                'Nota 2: ' + this.todos[i].n2.toFixed(1) + '\n' +
                'Nota 3: ' + this.todos[i].n3.toFixed(1) + '\n' +
                'Definitiva: ' + this.todos[i].definitiva.toFixed(1) + '\n' +
                this.todos[i].res + '\n\n';

            }
        }
    }
}


</script>


<style scoped>

    h1{
        color: bisque;
        width: fit-content;
        background-color: brown;
        border-radius: 20px;
    }
    span{
        color: whitesmoke;
    }
    .cuadro{
        top: 0px;
    }

    .alerta{
        top: 40px;
        width: 500px;
    }
    #nota{
        width: 40px;
    }

    #area{
        top: 20px;
        height: 400px;
        width:max-content;
    }
    #contenedor{
        top: 25px;
        background-color:cadetblue;
        width: 100px;
        border-radius: 10px;
        border-color: brown;
    }

    button{
        
    }
    textarea{
        top: 50px;
        width: 300px;
    }
    button:hover{
        cursor: pointer;
    }
    .area{
        top: 30px;
    }
    input{
        border-radius: 5px;
    }
</style>