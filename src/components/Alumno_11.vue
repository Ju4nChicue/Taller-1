<template>
    <body>
        <h1>Alumno</h1>

        <span>Nombre Estudiante: </span><input type="text" v-model="name" />

        <div id="cuadro">
        <span>Nombre Materia: </span><input type="text" v-model="course" />
        <span>Nota Materia: </span><input id="nota" type="number" min="0" max="5" v-model="nota" />
        <button @click="addCourse">Añadir</button>
        <button @click="deleteAll">Borrar Todo</button>
        </div>

        <h2 class="alerta" v-if="(name == null || course == null || nota == null) && (info.length < 3)">Llene todos los campos, por favor</h2>
        <h2 class="alerta" v-if="nota != null && (nota < 1 || nota > 5)">Ingrese una nota ente 1 y 5 incluyendolos</h2>

        <h2 class="alerta" v-if="info.length < 3">Despues de ingresar 3 materias, se moestrará el resultado</h2>

        <ul v-if="info.length == 3">
            <p>{{name}}</p>
            <li v-for="(x) in info">
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
        course: '',
        nota: null,
        info: []
    }
   },
   methods:{
    addCourse(){
            if(this.name != null || this.course != null || this.nota != null){
                if(this.info.length<3 && this.nota>0 && this.nota<=5){
                  
                    if(this.nota>=3){
                        let res = this.course + ': ' + this.nota.toFixed(1) + ' APROBADA';
                        this.info.push(res);
                    }
                    else{
                        let res = this.course + ': ' + this.nota.toFixed(1) + ' REPROBADA';
                        this.info.push(res);
                    }

                    this.course = null;
                    this.nota = null;
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
    }
</style>