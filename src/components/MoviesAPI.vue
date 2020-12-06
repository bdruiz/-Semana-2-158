<template>
<!-- Noticias -->
    <div id="news" class="container-fluid">
    <div class="row mt-md-5 mt-sm-5 mt-xs-5">
        <div class="col-lg-6 col-xs-12" v-for="(movie, index) of movies" :key="index">
            <div class="d-flex justify-content-center">

                <div class="p-3">
                    <img :src="movie.Poster" alt="Imagen de la pelicula">
                </div>

                <div class="p-4">
                    <h3>
                        {{movie.Title}}
                    </h3>
                    <p><strong>A&ntilde;o: </strong>{{movie.Year}}</p>
                    <p><strong>Tipo: </strong>{{movie.Type}}</p>
                    <p><strong>Código Internet Movie Database (IMDB): </strong>{{movie.imdbID}}</p>
                    <p class="text-justify">{{description_movies[index]}}</p>
                    <a :href="'https://www.imdb.com/title/'+movie.imdbID" target="_blank" class="btn btn-outline-info">Ver Pelicula en IMDB</a>
                </div>
            </div>
        </div>      
    </div>
</div>
<!-- End Noticias -->

    
</template>

<script>
import axios from 'axios'

    export default {
        name: "MoviesAPI",
        data(){
            return{
                movies: null,
                description_movies: []

            }
        },
        mounted(){
            axios
            .get('http://www.omdbapi.com/?s=fast&apikey=92be8ebd')
            .then(response => {
            (this.movies = response.data.Search.slice(0,4))
            console.log(this.movies)
                for(let i=0; i<this.movies.length;i++){
                    axios
                    .get('http://www.omdbapi.com/?i='+this.movies[i].imdbID+'&apikey=92be8ebd').then(
                    response => {
                    (this.description_movies.push(response.data.Plot))
                    console.log(this.description_movies)}
                    );
                }
            })
           // .get('http://www.omdbapi.com/?t=fast&plot=full&apikey=eccb44c')
           // .then(response=> {
            //    (this.movies=response.data)
            //    console.log(this.movies)
            
           // })
        }
    }
</script>

<style scoped>

</style>
