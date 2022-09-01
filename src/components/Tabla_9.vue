<template>
    <body>
        <h1>Creacion de Tabla con N filas y M columnas</h1>

        <span>Filas: </span><input class="num" type="number" v-model="nf" min="0"/>

        <span>  Columnas: </span><input class="num" type="number" v-model="mc" min="0"/>

        <table v-if="nf > 0 && mc>0">
            <tr v-for="(i) in nf">
                <td width="50" v-for="(j) in mc">{{i}},{{j}}</td>
            </tr>
        </table>

        <p v-else>Ingrese valores mayores a 0</p>
    </body>
</template>

<script>
export default {
    name: 'Tabla',
    data(){
        return{
            nf: null,
            mc: null
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