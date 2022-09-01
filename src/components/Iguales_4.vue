<template>

    <h1>Cuantos números son iguales?</h1>

    <p>Dame 3 números</p>
    <input type="number" v-model="n1"/>
    <span> - </span>
    <input type="number" v-model="n2"/>
    <span> - </span>
    <input type="number" v-model="n3"/>

    <div>
        <button @click="comparar" id="A" class="boton">Comparar</button>
    </div>

    <p>{{answer}}</p>

</template>

<script>
export default {
    name: 'Iguales',
    props:{},
    data(){
        return{
            n1: null,
            n2: null,
            n3: null,
            answer: ''
        }
    },
    methods:{
        comparar(){
            if(this.n1 == null || this.n2 == null || this.n3 == null){
                this.answer = 'Ingresa los 3 números, por favor';
            }
            else{
                
                let counter = 1;

                if(this.n1 == this.n2){
                    counter ++;
                }
                if(this.n1 == this.n3){
                    counter ++;
                }

                if(counter == 1){
                    if(this.n2 == this.n3){
                        this.answer = '2 de estos números, son el mismo'
                    }
                    else{
                        this.answer = 'Todos los numeros son diferentes';
                    }
                }
                else if(counter == 3){
                    this.answer = 'Todos los números son iguales';
                }
                else{
                    this.answer = counter + ' de estos números, son el mismo';
                }
            }
                
                
                }  
            }
        }
</script>

<style scoped>
    input{
        width: 40px;
    }
</style>