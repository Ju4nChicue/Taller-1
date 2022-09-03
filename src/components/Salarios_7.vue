<template>
  
    <h1>Salarios</h1>

    <p>Ingrese 10 salarios</p>

    <span>Salario: </span><input type="number" v-model="salary" min="0" />
    <button @click="addSalary" id="agregar">Ingresar</button>

    <button @click="deleteSalarys" id="borrar">Borrar todo</button>

    <div>
        <button @click="showSalarys" id="mostrar">Mostrar todos</button>
    </div>

    <textarea readonly id="area" cols="30" rows="10">{{answer}}</textarea>
    

</template>

<script>
export default {
    name: 'Salarios',
    data(){
        return {
            salary: null,
            salarys:[],
            answer: ''
        }
    },
    methods:{
        addSalary(){

            if(this.salarys.length < 10){
                if(this.salary>0){
                    this.salarys.push(this.salary);
                    this.answer = '';
                }
                else{
                    this.answer = 'Ingrese un valor mayor que 0';
                }
            }
            else{
                this.answer = 'No se pueden agregar más salarios (10 max)';
            }
            this.salary = null;
        },
        showSalarys(){
            if(this.salarys.length == 10){
                
                this.answer = '';

                for(let i = 0; i < this.salarys.length; i++){
                    this.answer += '$' + this.salarys[i] + ' aumentado 8% es: $' + (this.salarys[i]*1.08).toFixed(2) + '\n';
                }
            }
            else{
                this.answer = 'ERROR: INGRESE AL MENOS 10 SALARIOS, LLEVAS: ' + this.salarys.length;
            }
        },
        deleteSalarys(){
            this.answer = '';
            this.salarys = [];
        }

    }
}
</script>

<style scoped>
    #mostrar{
        position: relative;
        top: 10px;
    }
    #area{
        position: relative;
        top: 20px;
        resize: none;
        width: 300px;
    }
    h1{
        color: deepskyblue;
        font-family: fantasy;
    }
    p, span{
        color: beige;
        font-family:Georgia;
    }
    button{
        background-color: gray;
        color: white;
        border-radius: 5px;
    }
    button:hover{
        cursor: pointer;
        color: black;
    }
    #agregar:hover{
        background-color: greenyellow;
    }
    #borrar:hover{
        background-color: red;
    }
    textarea{
        border-radius: 5px;
        font-family: Impact;
        border: 3px solid red;
    }
    
</style>