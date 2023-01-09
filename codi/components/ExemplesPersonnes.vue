<template>
    <div>
        <v-card rounded style="background-color:#7a5fb7" width="600" class="ma-2 mb-5 mr-5">
           
                <v-card-title  cols="8" v-for="(n, i) in personnes" :key="n.nom">
                    <h3 class="fill-height">el nom es : {{n.nom}} y l'edat {{n.edat}}</h3>
                </v-card-title>
    
        </v-card>
        <v-card  shaped color="rgba(255, 10, 100, 0.7)">
            <v-text-field v-model="nom" label="nom"></v-text-field>
            <v-text-field v-model="edat" label="edat"></v-text-field>
            <v-btn @click="afegirPersona()">afegir persona</v-btn> 
        </v-card>
        <v-card color="rgba(200, 50, 200, 0.3)" width="600" class="ma-2 mb-5 mr-5">
                <v-col cols="12" align="center">
                    <v-btn @click="OrdenarNom()" outlined color="primary">OrdenarPerNom</v-btn> 
                    <v-btn @click=" OrdenarZA()" outlined background-color="primary">OrdenarNomZA</v-btn>
                    <v-btn @click="OrdenarEdat()"  outlined color="primary">OrdenarPerEdat</v-btn> 
                    <v-btn @click=" OrdenarEdatDesc()" outlined color="primary">OrdenarEdatDescandent</v-btn> 
                </v-col>
        </v-card>
        <v-card  shaped color="rgba(255, 10, 100, 0.7)">
            <v-card-title>
                Edat mes gran : {{edatMesGran}} anys
                <br>
                Edat mes petita : {{edatMesPetita}} anys
                <br>
                Mitjana d'edat: {{edatMitjana}}
            </v-card-title>
        </v-card>
    </div>
</template>

<script>
   
    export default {
        data(){
            return { 
                nom:"",
                edat:0,
                personnes : [
                {
                    nom:'John', edat:30
                },
                {
                    nom:'Barbara', edat:25
                },
                {
                    nom:'Emanuel', edat:45
                },
                {
                    nom:'Hicham', edat:21
                },
            ]
            }
        },
        methods:{
        OrdenarNom(){
            console.log("ya estat")
            this.personnes.sort((a,b) =>{
                if(a.nom < b.nom) return -1;
                if(a.nom > b.nom) return  1;
                return 0
             })
           
            },
            OrdenarZA(){
            console.log("ya estat")
            this.personnes.sort((a,b) =>{
                if(a.nom > b.nom) return -1;
                if(a.nom < b.nom) return  1;
                return 0
             })
           
            },
            OrdenarEdat(){
            console.log("ya estat")
            this.personnes.sort((a,b) =>{
                if(a.edat < b.edat) return -1;
                if(a.edat > b.edat) return  1;
                return 0
             })
           
            },
            OrdenarEdatDesc(){
            console.log("ya estat")
            this.personnes.sort((a,b) =>{
                if(a.edat > b.edat) return -1;
                if(a.edat < b.edat) return  1;
                return 0
             })
           
            },
            afegirPersona(){
                let novaPersona ={
                    nom:this.nom,
                    edat:this.edat
                }
                this.$set(this.personnes, this.personnes.length,novaPersona
                )
                this.nom=""
                this.edat=0
            }
        },
        computed:{
            edatMesGran(){
                let maxim = -Infinity
                this.personnes.forEach(
                    function(persona, posicio, array){
                        if(persona.edat > maxim){
                            maxim = persona.edat
                        }
                    }
                )
                return maxim
            },
            edatMesPetita(){
                let minim = +Infinity
                this.personnes.forEach(
                    function(persona, pos, array){
                        if(persona.edat< minim){
                            minim = persona.edat
                        }
                    }
                )
                return minim
            },
            edatMitjana(){
                let totalEdats = 0
                this.personnes.forEach(
                   (persona, pos, array) =>{
                           totalEdats += persona.edat
                        }
                )
                return totalEdats / this.personnes.length
            }
        }
     }
   
</script>

<style scoped>

</style>