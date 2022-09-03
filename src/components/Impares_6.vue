<template>

    <h1>Lista Número Impares</h1>

    <p>Digita un número y voy a listar los numeros impares menores al ingresado</p>

    <input type="number" v-model="number"/>

        <button @click="generateList" class="boton">Listar</button>

    <p v-if="number">Presione el boton para ver los numeros impares menores a {{number}}</p>

    <ul>
        <li v-for="(n) in numbers">
            <span>{{n}}</span>

        </li>
    </ul>

</template>

<script>
export default {
    name: 'Impares',
    data(){
        return{
            number: null,
            numbers: []
        }
    },
    methods:{
        generateList(){

            if(this.number != null){
                this.numbers = [];

                let num = this.number;
                if(this.number%2 == 0){
                    num --;
                    this.numbers.push(num);

                    while(num > 0){

                        num -= 2;
                        if(num > 0){
                            this.numbers.push(num);
                        }
                    }
                }
                else{
                    while(num > 0){

                        num -= 2;
                        if(num > 0){
                            this.numbers.push(num);
                        }
                    }
                }
            }
        }
    }
}
</script>

<style scoped>
    h1{
        font-family: 'Times New Roman';
        color: coral;
    }
    p{
        color:antiquewhite;
    }

    input{
        background-color: grey;
        width: 80px;
        color: white;
    }

    button{
        background-color: cornflowerblue;
        border-radius: 5px;
    }
    button:hover{
        cursor: pointer;
    }

    span{
        color: cornflowerblue;
    }
</style>