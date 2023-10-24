<template >
    <ul  class="movie-list list-group">
        <MovieListItem v-for="movie in movies" 
        :movie="movie"
        :key="movie.id"
        @onlike="$emit('onLike',movie.id,)"
        @onfavorite = "$emit('onfavorite', movie.id)"
        @onRemove = "$emit('onRemove', $event)"
        />
    </ul>
</template>


<script lang = "ts">
import MovieListItem from "../movie-list-item/MovieListItem.vue"

export default {
    components: { MovieListItem },
    props:{
        movies:{
            type: Object,
            required: true,
        },
    },
}
</script>
<style scoped>
.movie-list {
    margin-top: 2rem;
    min-height: 50px auto;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>