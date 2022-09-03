<template>

    <h1>Lista Ordenada</h1>

    <p>Digita un número</p>

    <input type="number" placeholder="Presione enter" v-model="number" @keypress.enter="addNumber"/>

    <div>
        <button @click="deleteList" class="boton">Borrar todo</button>
    </div>

    <ul>
        <li v-for="(n) in numbers">
            <span>{{n}}</span>
        </li>
    </ul>

</template>

<script>
export default {
    name: 'ListaOrdenada',
    data(){
        return{
            number: null,
            numbers: []
        }
    },
    methods:{
        addNumber(){
            if(this.number != null){

                this.numbers.push(this.number);

                this.numbers.sort((a,b) =>{return a - b;});

                this.number = null;
            }
        },
        deleteList(){
            this.numbers = [];
        }
    }
}
</script>

<style scoped>
    h1{
        color: aquamarine;
        font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }

    p{
        color: white;
        font-family: 'Times New Roman', Times, serif;
    }

    input{
        border-color: red;
        border-style:double;
        border-radius: 5px;
    }
    button{
        border-radius: 6px;
    }
    button:hover{
        cursor: pointer;
        background-color: aqua;
    }
    span{
        color: white;
        font-family: 'Courier New', Courier, monospace;
    }
    
</style>