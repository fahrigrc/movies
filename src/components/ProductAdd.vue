<template>
    <div id="add-form">
        <form @submit.prevent="handleAdd">
            <div class="form-group">
                <label for="id">id</label>
                <input v-model="movie.id" type="text" class="form-control" id="id">
            </div>
            <div class="form-group">
                <label for="name">İsim</label>
                <input v-model="movie.name" type="text" class="form-control" id="name">
            </div>
            <div class="form-group">
                <label for="director">Yönetmen</label>
                <input v-model="movie.director" type="text" class="form-control" id="director">
            </div>
            <div class="form-group">
                <label for="year">Yıl</label>
                <input v-model="movie.year" type="text" class="form-control" id="year">
            </div>
            <div class="form-group">
                <label for="image">Fotoğraf</label>
                <input v-model="movie.image" type="text" class="form-control" id="image">
            </div>
            <button type="submit" class="btn btn-success">Ekle</button>
        </form>
    </div>

</template>
<script>
export default {
    name: "product-add",
    data() {
        return {
            movie: {id:'', name:'',director:'',year:'',image:''}
        }
    },
    methods: {
        handleAdd(){
            this.$emit("add:movie",this.movie)
        }
    }

}
</script>
<style scoped>


</style>