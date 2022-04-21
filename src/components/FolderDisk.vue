<template>

   <main>

       <!-- componente che seleziona il genere musicale -->
       <!-- viene importato il valore selezionato e avvia il metodo changeSelect -->
       <GenreSelection @selectedGenre="changeSelect"/>

       <section>

           <!-- v-for che cicla i dati dell api -->
           <!-- nella seconda milestone, utilizzo nel v for la funzione scritta in computed -->
           <!-- la funzione filteredRecordList mi genera l'array in base alla selezione -->
           <!-- con il v-bind mando al figlio i singoli dati -->
           <DiskCard
           v-for="( element, index ) in filteredRecordList"
           :key="index"
           :poster="element.poster"
           :title="element.title"
           :author="element.author"
           :year="element.year"
           />

       </section>

   </main>
    
</template>



<script>
import DiskCard from '@/components/DiskCard.vue';
import GenreSelection from '@/components/GenreSelection.vue';

import axios from "axios";

export default {
    name: 'FolderDisk',

    components: {
        DiskCard,
        GenreSelection,
    },

    data(){
        return{
            // impostiamo array vuoto da riempire con i dati
            // del api esterno inerenti ai dischi
            diskArray:[],
            // valore vuoto che raccogliera la selezione dell utente
            selectedGenre : ''
        }
    },

    created(){
        //qui utilizziamo axios
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
             .then( (res) => {
                 console.log(res.data.response);
                 this.diskArray = res.data.response
             })
             .catch( (error) => {
                 console.log( error )
             })
    },

    computed : {
        // filtra l'array degli elementi della pagina in base al valore di selectedGenre, impostato con il metodo changeSelect
        filteredRecordList(){
            if (this.selectedGenre === 'all') {
                return this.diskArray;
            }

            return this.diskArray.filter((item) => {
                return item.genre
                   .toLowerCase()
                   .includes(this.selectedGenre.toLowerCase());
            })
        }
    },

    methods: {
        // imposta selectedGenre(valore salvato nei data) con il valore della selezione dell'utente
        changeSelect(selezione){
            this.selectedGenre = selezione
            console.log(this.selectedGenre);
        }
    }
}

</script>



<style scoped lang="scss">

main {
    section {
        width: 60%;
        margin: 30px auto 0;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }
}

</style>
