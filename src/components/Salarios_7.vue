<template>
  
    <h1>Salarios</h1>

    <p>Ingrese 10 salarios</p>

    <span>Salario: </span><input type="number" v-model="salary" min="0" />
    <button @click="addSalary">Ingresar</button>

    <button @click="deleteSalarys">Borrar todo</button>

    <div>
        <button @click="showSalarys" id="borrar">Mostrar todos</button>
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
        },
        showSalarys(){
            if(this.salarys.length == 10){
                
                this.answer = '';

                for(let i = 0; i < this.salarys.length; i++){
                    this.answer += '$' + this.salarys[i] + ' aumentado 8% es: $' + this.salarys[i]*1.08 + '\n';
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
    #borrar{
        position: relative;
        top: 10px;
    }
    #area{
        position: relative;
        top: 20px;
    }
</style>