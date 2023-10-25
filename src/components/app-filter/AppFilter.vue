<template >
    <div class="btn-group">
        <button class="btn btn-dark" type="button" @click="AllMovies">
            Barcha kinolar
        </button>
        <button class="btn btn-outline-dark" type="button" @click="FavoriteMovies">
            Mashhur kinolar
        </button>
        <button class="btn btn-outline-dark" type="button" @click="ViewMovies">
            Eng ko'p ko'rilgan kinolar
        </button>
    </div>
</template>



<script lang="ts" >
export default {
    data() {
        return {
            allmovies: true,
            viewmovies: false,
            favoritemovies: false,
        }
    },
    methods:
    {
        AllMovies() {
            const checkmovies = {
                allmovies: true,
                viewmovies: false,
                favoritemovies: false,
            }
            this.$emit('AllMovies', checkmovies)
        },
        ViewMovies() {
            const checkmovies = {
                allmovies: false,
                viewmovies: true,
                favoritemovies: false,
            }
            this.$emit('AllMovies', checkmovies)
        },
        FavoriteMovies() {
            const checkmovies = {
                allmovies: false,
                viewmovies: false,
                favoritemovies: true,
            }
            this.$emit('AllMovies', checkmovies)
        },
    }
}
</script>


<style ></style>