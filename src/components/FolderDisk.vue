<template>

   <main>

       <section>

           <DiskCard/>

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

</style>
