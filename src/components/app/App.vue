<template>
    <div class="app font-monospace ">
        <div class="content">
            <AppInfo :allMoviesCount="movies.length" :favoriteMoviesCount="movies.filter(c => c.favorite).length" />
            <div class="search-panel">
                <SearchPanel @searchMovie="SearchMovieHandler" />
                <AppFilter @AllMovies="AllMoviesHandler" @ViewMovies="AllMoviesHandler"
                    @FavoriteMovies="AllMoviesHandler" />
            </div>
            <MovieList :movies="filteredMovies(allmovies, viewmovies, favoritemovies, movies, term)" @onLike="onLikeHandler"
                @onfavorite="onfavoriteHandler" @onRemove="onRemoveHandler" />
            <MovieAddForm @createMovie="createMovie" />
        </div>
    </div>
</template>


<script lang="ts">
import AppInfo from "../app-info/AppInformation.vue"
import SearchPanel from "../search-panel/SearchPanel.vue"
import AppFilter from "../app-filter/AppFilter.vue"
import MovieList from "../movie-list/MovieList.vue"
import MovieAddForm from "../movie-add-from/MovieAddForm.vue"
export default {
    components: {
        AppInfo,
        SearchPanel,
        AppFilter,
        MovieList,
        MovieAddForm,
    },
    data() {
        return {
            allmovies: true,
            viewmovies: false,
            favoritemovies: false,
            term: '',
            movies: [
                {
                    name: 'Samandarbek',
                    viewars: 811,
                    favorite: false,
                    like: true,
                    id: 1,
                },
                {
                    name: 'Yigitaliyev',
                    viewars: 121,
                    favorite: false,
                    like: false,
                    id: 2,
                },
                {
                    name: 'Tashkent',
                    viewars: 124,
                    favorite: false,
                    like: false,
                    id: 3
                },
                {
                    name: 'Tashkent',
                    viewars: 124,
                    favorite: true,
                    like: false,
                    id: 4,
                },
            ],
        }
    },
    methods: {
        AllMoviesHandler(checkmovies: any) {
            this.allmovies = checkmovies.allmovies
            this.viewmovies = checkmovies.viewmovies
            this.favoritemovies = checkmovies.favoritemovies
        },
        filteredMovies(allmovies: boolean, viewmovies: boolean, favoritemovies: boolean, arr: any, term: any) {
             if (term.length !== 0) {
                return arr.filter(c => c.name.indexOf(term) > -1);
            }
            
            else if (allmovies) {
                return arr;
            }

            else if (viewmovies) {
                const maxViewars = Math.max(...arr.map(movie => movie.viewars));
                return arr.filter(movie => movie.viewars === maxViewars);
            }

            else if (favoritemovies) {
                // Filter movies based on favoritemovies criteria.
                return arr.filter(c => c.favorite == true);
            }


            else if (term.length == 0) {
                return arr;
            }
            else {
                // Handle other cases or return an empty array.
                return [];
            }
        },
        createMovie(e: any) {
            this.movies.push(e)
        },

        onLikeHandler(id: any) {
            this.movies = this.movies.map(item => {
                if (item.id == id) {
                    item.like = !item.like
                }
                return item
            })
        },
        onfavoriteHandler(id: any) {
            this.movies = this.movies.map(item => {
                if (item.id == id) {
                    item.favorite = !item.favorite
                }
                return item
            })
        },
        onRemoveHandler(id: any) {
            console.log(id)
            this.movies = this.movies.filter(c => c.id !== id)
        },
        SearchMovieHandler(term: string) {
            this.term = term
            console.log(this.term)
        }
    }
}

</script>

<style>
.app {
    height: 100vh;
    color: black;
}

.content {
    width: 1000px;
    min-height: 700px;
    background-color: azure;
    margin: 0 auto;
    padding: 2rem 0;
}

.search-panel {
    margin-top: 2rem;
    min-height: 50px auto;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>