<template>
  <div id="app">
    <ProductAdd @add:movie="addMovie" />
    <ProductList @update:movie="updateMovie" @delete:movie="deleteMovie" :movies= "movies"/>
    
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue'
import ProductAdd from './components/ProductAdd.vue'

export default {
  name: 'App',
  components: {
    ProductList,ProductAdd
  },
  data() {
    return {
      movies: [
        {id: 1, name:'Düğün Dernek' , director : 'Selçuk Aydemir', year: 2013 , image : 'https://tr.web.img3.acsta.net/pictures/14/03/20/10/14/061444.jpg' },
        {id: 2, name:'Düğün Dernek' , director : 'Selçuk Aydemir', year: 2013 , image : 'https://tr.web.img3.acsta.net/pictures/14/03/20/10/14/061444.jpg' },
        {id: 3, name:'Düğün Dernek' , director : 'Selçuk Aydemir', year: 2013 , image : 'https://tr.web.img3.acsta.net/pictures/14/03/20/10/14/061444.jpg' }
      ],
      searchKey: '',
      moviesList : []
      
    }
  },
  mounted() {
    if(localStorage.getItem('movies')) {
      try {
        this.movies = JSON.parse(localStorage.getItem('movies'));
      } catch(e) {
        localStorage.removeItem('movies');
      }
    }
  },
  methods: {
    deleteMovie(movie){
      this.movies = this.movies.filter(
        movieToFilter => movieToFilter.id !== movie.id
      )
    },
    updateMovie(){
       
    },
    addMovie(movie) {
      const newMovie = {...movie}
      this.movies = [...this.movies, newMovie]
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 100px;
}

</style>
