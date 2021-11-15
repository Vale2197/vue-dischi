<template>
    <main>
        <div class="container-fluid">
            <div class="row px-3">
                 <singleCard v-for="disco in dischiList" :key="disco.author"
                   :immagine="disco.poster" />
            </div>
        </div>
    </main>
</template>

<script>
import singleCard from "./singleCard.vue"
import axios from "axios" 

export default{
    components: {
        singleCard
    },
   name: "siteMain",

   /* 
        DATA 
    */
     data() {
        return {
            dischiList: []
        }
    },

    mounted() {
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(r => {
                console.log(r.data.response);
                this.dischiList = r.data.response;
                console.log(this.dischiList);
            })
            .catch(e => {
                console.log(e);
            })
    }
}
</script>

<style lang="scss">

</style>
