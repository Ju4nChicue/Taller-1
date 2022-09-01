<template>
    <body>
        <h1>Creacion de Tabla con N filas y M columnas</h1>

        <span>Numero de columnas: </span><input class="num" type="number" v-model="nf" />

        <span> Agregar número: </span><input class="num" type="number" v-model="num" @keypress.enter="addNumber"/>

        <button @click="addColum">Añadir col</button>


        <table>
            <td width="50" v-for="(i) in tabla.length">
                <tr v-for="(j) in tabla.length">{{tabla[j]}}</tr>
            </td>
        </table>
      
    </body>
</template>

<script>
export default {
    name: 'Suma_Matriz',
    data(){
        return{
            nf: null,
            num: null,
            col: [],
            tabla: []
        }
    },
    methods:{
        addNumber(){

            this.col.push(this.num);
            console.log(this.col)
        },
        addColum(){
            this.tabla.push(this.col);
            this.col = [];
        }
    }
}
</script>

<style scoped>
   
   .num{
    width: 40px;
   }

   table{
    top: 10px;
    background-color: white;
    color: black;
    border: 5px solid blue;
   }

   td, tr{
    border: 1px solid black;
   }
   
</style>