<template>
    <div> 
        <h1>Suma Matriz</h1>

        <input type="number" v-model="filas" placeholder="Filas" min="0">
        <button @click="create" v-if="colum > 0 && filas > 0" > Presiona para crea tabla </button>

        <br>

        <input type="number" v-model="colum" placeholder="Columnas" min="0" @keyup="sum=new Array(colum)">
        <button @click="suma" v-if="colum > 0 && filas > 0" > Sumar </button>

          <p>
            <table>
              <tbody>
                <tr v-for="(row,i) in filas">
                    <td v-for="(col,j) in colum">
                        <input type="number" placeholder="Valor" min="0" @keyup="add($event,i,j)">
                    </td>
                </tr>
                <tr v-if="sum[sum.length-1]!=null">
                  <td v-for="(col,i) in colum"> {{sum[i]}}</td>
                </tr>
              </tbody>
            </table>
          </p>
    </div>
</template>

<script>
  export default {
    name: 'Tabla',
    data(){
        return{
            colum :'',
            filas: '',
            matrix: [],
            sum: [],

        }
    },
    methods: {
        create(){
            this.matrix = new Array(this.filas);
            for (let i = 0; i < this.filas; i++) {
                this.matrix [i] = new Array(this.colum)

            }
        },
        add(event,i,j){
          this.matrix[i][j]= parseInt(event.target.value);
        },
        suma(){
        for (let col = 0; col < this.matrix[0].length; col++) {
            let sumCol = 0;
            for (let row = 0; row < this.matrix.length; row++) {
              sumCol+= this.matrix[row][col];
            }
          this.sum[col]= sumCol; 
        }
      }
    }
}
</script>

<style scoped>
button{
    border-radius: 5px;
    color: cadetblue;
    background-color: black;
    border: 2px white;
}
button:hover{
    cursor: pointer;
}
input{
    border-radius: 4px;
    border-color: blue;
}
h1{
    color: rgba(255, 0, 0, 0.753);
}

</style>