<template >
    <li class="list-group-item d-flex justify-content-between" :class="[{ like: movie.like }, { favorite: movie.favorite }]">
        <span @click="onLike" class="list-group-item-label">{{ movie.name }}</span>
        <input type="number" class='list-group-item-input' :value=movie.viewars />
        <div class="d-flex justify-content-center aligin-items-center">
            <button @click ="$emit('onfavorite', movie.id)" type="button" class="btn">
                <i class='bx bxs-bookmark-star'></i>
            </button>
            <button type="submit" class="btn" @click = "$emit('onRemove', movie.id)">

                <i class='bx bx-trash bx-sm'></i>

            </button>
            <i class="icon-star fas fa-star "></i>
        </div>
    </li>
</template>

<script lang="ts">
import 'boxicons'
export default {
    props: {
        movie: {
            type: Object,
            required: true,
        },
    },
    methods: {
        onLike() {
            this.$emit('onlike', this.movie.id)
        }
    }
}
</script>


<style>
.list-group-item {
    padding: 15px 20px;
    border-bottom: 1px solid #3d5a80;
}

.list-group-item:last-child {
    border-bottom: none;
}

.list-group-item span {
    line-height: 35px;
    font-size: 20px;
    cursor: pointer;
    width: 550px;
}

.list-group-item input {
    line-height: 35px;
    font-size: 20px;
    text-align: center;
    border: 0;
    outline: none;
}

.list-group-item button {
    margin: 3px;
    font-size: none;
    cursor: pointer;
}

.list-group-item .btn-cookie {
    color: #e09f3e;
    border-radius: 25px;
    border-color: rgb(0, 255, 55);
}

.list-group-item .btn-trash {
    border-color: transparent;
    color: transparent;
    text-align: center;
    padding: 0rem;
}

.list-group-item .icon-star {
    width: 35px;
    height: 35px;
    text-align: center;
    line-height: 35px;
    font-size: 16px;
    color: #ffd700;
    transition: 0.3s all;
    transform: translateX(30px);
    opacity: 0;
}

.list-group-item.like .icon-star {
    opacity: 1;
    transform: translateX(0);
}

.list-group-item.favorite .list-group-item-label,
.list-group-item.favorite .list-group-item-input {
    color: #e09f3e
}

.custom-color {
    color: blue;
}
</style>