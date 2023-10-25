<template>
    <input type="text" class="form-control search-input" :value='searchInput' 
        @input="searchInput = $event.target.value"
        @keydown.enter="Send"
        placeholder="Kinolarni qidirish" />
</template>


<script lang="ts">
export default {
    data() {
        return {
            searchInput: ''
        }
    },
    methods: {
        Send() {   
            const searchMovie = this.searchInput
            this.$emit('searchMovie', searchMovie)
            // this.$nextTick(() => {
            //     this.searchInput = '';
            // });
        }
    },
}
</script>
<style scoped>
.search-input {
    margin-bottom: 1rem;
    min-height: 50px auto;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>