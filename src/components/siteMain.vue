<template>
    <main>
        <div class="container-fluid">
            <div class="my_select col-12">
                <span>
                    Ricerca per genere: 
                </span>
                <select @change="change_genre($event)" name="select" id="select_genere">
                        <option value="1">
                            Mostra tutto
                        </option>
                        <!--  -->

                        <option value="2">
                            Rock
                        </option>
                        <!--  -->

                        <option value="3">
                            Pop
                        </option>
                        <!--  -->

                        <option value="4">
                            Jazz
                        </option>
                        <!--  -->

                        <option value="5">
                            Metal
                        </option>
                        <!--  -->

                </select>
            </div>

            <div v-if="dischiList.length == 10 && select_genre == 1" class="row px-3">
                 <singleCard v-for="disco in dischiList" :key="disco.author"
                   :immagine="disco.poster" 
                    :titolo="disco.title"
                    :author="disco.author"
                    :year="disco.year"
                />
            </div>
            <div v-else-if="select_genre > 1" class="row">
                <singleCard v-for="disco in filterList" :key="disco.author"
                   :immagine="disco.poster" 
                    :titolo="disco.title"
                    :author="disco.author"
                    :year="disco.year"
                    />
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
            select_genre: 1,
        }
    },
    mounted() {

        setTimeout(() => {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(r => {
                this.dischiList = r.data.response;
                console.log(this.dischiList);
            })
            .catch(e => {
                console.log(e);
            })
        }, 2000);        
    },

    methods: {
        change_genre(event) {
            this.select_genre = parseInt(event.target.value); 
            console.log(this.select_genre);
        }
    },
    computed: {
        filterList() {
           return this.dischiList.filter((disco) => {
                if(this.select_genre == 2 && disco.genre == "Rock") {
                   return disco
                }
                else if(this.select_genre == 3 && disco.genre == "Pop") {
                   return disco
                }
                else if(this.select_genre == 4 && disco.genre == "Jazz") {
                   return disco
                }
                else if(this.select_genre == 5 && disco.genre == "Metal") {
                   return disco
                }
            })
        }
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

        .my_select {
            margin-top: 2rem;
            span {
                color: #777e7d;
                font-weight: bold;
                font-size: 1.5rem;
                margin-right: 1rem;
            }
            select {
                background-color: $bg_card;
                color: #777e7d;
                border: 1px solid #777e7d;
                font-weight: bold;
                font-size: 1.5rem;
                border-radius: 0.5rem;
                box-shadow: 2px 2px 2px black;
                padding: 0.5rem 2rem;
            }

        } 
    }
</style>
