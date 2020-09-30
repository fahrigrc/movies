<template>
    <div id="list">
        <p v-if="movies.length==0"> Film listesi boş</p>
        <table v-else class="table">
            <thead>
                <tr>
                    <th>id</th>
                    <th>Film Adı</th>
                    <th>Yönetmen</th>
                    <th>Yıl</th>
                    <th>Afiş</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="movie in movies" :key="movie.id">
                    <td v-if="updateId === movie.id">
                        <input v-model="movie.id" type="text" class="form-control" id="id">
                    </td>
                    <td v-else>{{movie.id}}</td>
                    <td v-if="updateId === movie.id">
                        <input v-model="movie.name" type="text" class="form-control" id="name">
                    </td>
                    <td v-else>{{movie.name}}</td>
                    <td v-if="updateId === movie.id">
                        <input v-model="movie.director" type="text" class="form-control" id="director">
                    </td>
                    <td v-else>{{movie.director}}</td>
                    <td v-if="updateId === movie.id">
                        <input v-model="movie.year" type="text" class="form-control" id="year">
                    </td>
                    <td v-else>{{movie.year}}</td>
                    <td v-if="updateId === movie.id">
                        <input v-model="movie.image" type="text" class="form-control" id="image">
                    </td>
                    <td v-else><img v-bind:src="movie.image" alt="" ></td>
                    <td  v-if="updateId !== movie.id">
                        <button class="btn-small btn-primary" @click="handleUpdate(movie)">Güncelle</button>
                        <button class="btn-small btn-danger" @click="handleDelete(movie)">Sil</button>
                    </td>
                    <td v-else>
                        <button class="btn-small btn-primary" @click="handleSave(movie)">Kaydet</button>
                        <button class="btn-small btn-danger" @click="updateId=null">İptal</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    name:"movie-list",
    data(){
        return {
            updateId:null
        }
    },
    props: {
        movies: Array
    },
    methods: {
        handleDelete(movie){
            this.$emit("delete:movie",movie)
        },
        handleUpdate(movie){
            this.updateId = movie.id
        },
        handleSave(movie){
            this.$emit("update:movie",movie)
            this.updateId = null
        }
    }   
}
</script>
<style scoped>
img{
    max-width: 300px;
    max-height: 300px;
}
</style>