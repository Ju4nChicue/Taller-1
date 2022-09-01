<template>

    <body>
        <h1>Dividir por el número en la posición indicado</h1>

        <input type="number" v-model="indice" min="0"/>
        
        <button @click="dividir">Calcular</button>

        <p v-if="indice<=0">Ingrese un número mayor a 0</p>

        <div>  
            <button id="bGenerar" @click="nuevaLista">Generar nuevos numeros</button>
        </div>

        <table id="tabla">
            <td width="150">
                <p v-if="lista.length>0">Lista actual:</p>
                <p v-for="(n,i) in lista">
                    <span>{{i+1}}. {{n}}</span>
                </p>
            </td>

            <td>
                <p v-if="lista2.length>0">Lista dividida por: {{lista[indice-1]}}</p>
                <p v-for="(n) in lista2">
                    <span>{{n}}</span>
                </p>
            </td>
        </table>
    </body>


</template>

<script>
export default {
    name: 'Indice',
    data(){
        return {
            indice: null,
            lista: [],
            lista2: []
        }
    },
    methods:{
        nuevaLista(){
            this.lista = [];
            this.lista2 = [];

            for(let i=0; i<10; i++){
                this.lista.push((Math.random()*10).toFixed(2));
            }
        },
        dividir(){
            
            this.lista2 = [];

            if(this.indice>0 && this.lista.length>0){
                

                for(let i=0; i<10; i++){
                    this.lista2.push((this.lista[i]/this.lista[this.indice-1]).toFixed(2));
                }
            }
        }
    }

}
</script>
<style scoped>
    #bGenerar{
        top: 10px;
    }
    #tabla{
        top: 20px;
    }
</style>