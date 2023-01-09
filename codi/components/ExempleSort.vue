<template>
    <div>
        <h3>Exemple sort</h3>
        <pre> {{edats}}</pre>
        <v-btn @click="sortDescandement()">Sort Descandement</v-btn>
        <pre>
            {{edats}}
        </pre>
        <v-btn @click="ordenarAsc()">Ordenar Ascendent</v-btn>
        <pre>
            {{edats}}
        </pre>
    </div>
</template>

<script>
    export default {
        mounted(){
      const nums = [10, 5, 8, 1, 7]
      nums.sort((a,b) => a-b)
      console.log(nums);
      this.edats = nums
    },
    data(){
       return {
        edats: [],
      }

    },
    methods:{
        sortDescandement(){
           let contador = 0
           this.edats.sort((a,b) => {
            console.log(this.edats)
                console.log(a,b)
                contador++
                return b-a 
           })
           
        },
        ordenarAsc(){
           
           this.edats.sort((a,b) => {
                return a-b 
           })
           
        },
    }
    }
</script>

<style scoped>

</style>