<template>
    <main>
        <div class="container-fluid">
            <div v-if="dischiList.length == 10" class="row px-3">
                 <singleCard v-for="disco in dischiList" :key="disco.author"
                   :immagine="disco.poster" 
                    :titolo="disco.title"
                    :author="disco.author"
                    :year="disco.year"/>
            </div>
            <div v-else class="row">
                <div class=" loading col-12">
                    <h2>
                        CARICAMENTO...
                    </h2>
                </div>
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
            dischiList: [],
            genreList:[],
        }
    },
    mounted() {

        setTimeout(() => {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(r => {
                this.dischiList = r.data.response;
                console.log(this.dischiList);

                this.genreList = this.dischiList.map((disco) => {
                    return disco.genre;
                }) 
                console.log(this.genreList);
            })
            .catch(e => {
                console.log(e);
            })
        }, 1000);
        
    }
}
</script>

<style lang="scss">
@import "../assets/variabili.scss";

    main {
        color: white;
        .row {
            padding: 6rem 0;
            p {
                margin: 0;
            }
        }

        .loading {
            text-align: center;

            h2 {
                width: 50%;
                margin: auto;
                padding: 0.5rem 3rem;
                background-color: $bg_card;
                border-radius: 1rem;
                box-shadow: 2px 2px 2px black;
            }
        }
    }
</style>
