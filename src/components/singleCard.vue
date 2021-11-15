<template>
    <div class="singleCard col-2">

        <div class="my_card">
            <div class="img">
            <img class="img-fluid" :src="immagine" alt="#">
            </div>
            <h3>
                {{titolo}}
            </h3>

            <div class="description">
                <p class="fs-5">
                    {{author}}
                </p>
                <p class="fs-5">
                    {{year}}
                </p>
            </div>
        </div>


    </div>
</template>


<script>

export default {
    name: "singleCard",
     props: {
        immagine: String,
        titolo: String,
        author: String,
        year: String
    } 
}
</script>


<style lang="scss">
@import "../assets/variabili.scss";

    .singleCard {
        text-align: center;
        font-weight: bold;
        margin-bottom: 2rem;

        .my_card{
            height: 100%;
            background-color: $bg_card;
            padding: 2rem 0;
            border-radius: 1rem;
            box-shadow: 2px 2px 2px black;

            .img {
                width: 80%;
                margin: auto;
            }
            
            h3 {
                width: 80%;
                margin: auto;
            }
            
            .description {
                color: #777e7d;
            }


        }
    }
</style>