<template>
    <header>
        <div class="container-fluid">
            <div class="row justify-content-between align-items-center p-3">
                <div class="logo col-2">
                    <img class="img-fluid" src="../assets/Spotify_logo_without_text.svg" alt="logospotify">
                </div>
            </div>
        </div>
    </header>
</template>

<script>

export default {
    name: "siteHeader",
}
</script>

<style lang="scss">
    @import "../assets/variabili.scss";

    header {
        background-color: $bg_card;

        .logo {
            width: 80px;
        }
    }

</style>
