<template >
    <div class="movie-add-form">
        <h3>Yangi Kino qo'shish</h3>
        <form class="add-form d-flex" @submit.prevent>
            <input type="text" class="form-control new-movie-lable" placeholder="qanday kino" :value='name'
                @input="name = $event.target.value" />
            <input type="text" class="form-control new-movie-lable" placeholder="Necha marotaba ko'rilgan?" :value="viewars"
                @input="viewars = $event.target.value" />
            <button class="btn btn-outline-dark" type="submit" @click="addMovie">
                Qo'shish
            </button>
        </form>
    </div>
</template>
<script lang="ts">
export default {
    data() {
        return {
            name: '',
            viewars: '',
        }
    },
    methods: {
        addMovie() {
            if(!this.name || !this.viewars) return
            const newMovie = {
                name: this.name,
                viewars: this.viewars,
                favorite: false,
                like: false,
                id: Date.now(), 
            }
            this.$emit('createMovie', newMovie)
            this.name = ''
            this.viewars = ''
        }
    }
}
</script>
<style> .movie-add-form {
     margin-top: 2rem;
     min-height: 50px auto;
     padding: 1.5rem;
     background-color: #fcfaf5;
     border-radius: 4px;
     box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
 }
</style>