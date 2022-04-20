<template>

   <main>

       <section>

           <!-- v-for che cicla i dati dell api -->
           <!-- con il v-bind mando al figlio i singoli dati -->
           <DiskCard
           v-for="( element, index ) in diskArray"
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

import axios from "axios";

export default {
    name: 'FolderDisk',
    components: {
        DiskCard,
    },
    data(){
        return{
            // impostiamo array vuoto da riempire con i dati
            // del api esterno inerenti ai dischi
            diskArray:[]
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
    }
}

</script>



<style scoped lang="scss">

main {
    section {
        width: 65%;
        margin: 50px auto 0;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }
}

</style>
