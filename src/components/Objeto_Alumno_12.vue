<template>
    <body>
        <h1>Guardar Alumno</h1>

        <span>Nombre Estudiante: </span><input type="text" v-model="name" />


        <div class="cuadro">
            <span>Nombre Materia 1: </span><input type="text" v-model="course1" />
            <span>Nota Materia 1: </span><input id="nota" type="number" min="0" max="5" v-model="nota1" />
        </div>
   
        <div class="cuadro">
            <span>Nombre Materia 2: </span><input type="text" v-model="course2" />
            <span>Nota Materia 2: </span><input id="nota" type="number" min="0" max="5" v-model="nota2" />
        </div>

        <div class="cuadro">
            <span>Nombre Materia 3: </span><input type="text" v-model="course3" />
            <span>Nota Materia 3: </span><input id="nota" type="number" min="0" max="5" v-model="nota3" />
        </div>

        <div class="cuadro">
            <button @click="addCourse">Añadir</button>
            <button @click="generarReporte">Reporte</button>
        </div>

        <div class="cuadro">
            <textarea readonly id="area" v-if="reporte" >{{reporte}}</textarea>
        </div>


        <h2 class="alerta">Si no llena todos los campos o si no ingresa notas entre 1 y 5 inclutendolos, no se ingresará</h2>



        <ul v-if="todos.length == 3">
            <li v-for="(x) in todos">
                {{x}}
            </li>
        </ul>

    </body>
</template>

<script>
export default {
   name: 'Alumno',
   data(){
    return{
        name:null,
        course1: '',
        nota1: null,
        course2: '',
        nota2: null,
        course3: '',
        nota3: null,
        todos: [],
        reporte: ''
    }
   },
   methods:{
    addCourse(){
            if(this.name != null || this.course1 != null || this.nota1 != null || this.course2 != null || this.nota2 != null || this.course3 != null || this.nota3 != null){
                if(this.todos.length<3 && this.nota1>0 && this.nota1<=5 && this.nota2>0 && this.nota2<=5 && this.nota3>0 && this.nota3<=5){

                    let alumno = {nombre: this.name, 
                                curso1: this.course1, 
                                curso2: this.course2,
                                curso3: this.course3,
                                n1: this.nota1,
                                n2: this.nota2,
                                n3: this.nota3,
                                res1: '',
                                res2: '',
                                res3: ''
                                };

                    if(this.nota1>=3){
                        alumno.res1 = 'APROBADO';
                    }
                    else{
                        alumno.res1 = 'REPROBADO';
                    }

                    if(this.nota2>=3){
                        alumno.res2 = 'APROBADO';
                    }
                    else{
                        alumno.res2 = 'REPROBADO';
                    }

                    if(this.nota3>=3){
                        alumno.res3 = 'APROBADO';
                    }
                    else{
                        alumno.res3 = 'REPROBADO';
                    }

                    this.todos.push(alumno)

                    this.name = null;
                    this.course1 = null;
                    this.nota1 = null;
                    this.course2 = null;
                    this.nota2 = null;
                    this.course3 = null;
                    this.nota3 = null;

                    console.log(this.todos)
                }
            }
    },
    generarReporte(){
        this.reporte = '';
        for(let i = 0; i < this.todos.length; i++){
            this.reporte += 'Alumno: ' + this.todos[i].nombre + '\n\n' +
                            this.todos[i].curso1 + ': ' + this.todos[i].n1 + ' ' + this.todos[i].res1 +  '\n' +
                            this.todos[i].curso2 + ': ' + this.todos[i].n2 + ' ' + this.todos[i].res2 +  '\n' +
                            this.todos[i].curso2 + ': ' + this.todos[i].n2 + ' ' + this.todos[i].res2 +  '\n\n';
        }
    }
   }
}
</script>


<style scoped>
    .cuadro{
        top: 30px;
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
        width:500px;
    }
</style>