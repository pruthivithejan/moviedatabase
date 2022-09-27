<script context="module">
    export async function load({fetch, params}){
        const res = await fetch(
            `https://api.themoviedb.org/3/movie/${params.id}?api_key=a18f9113593963ef65c47ef3c414f1f9&language=en-US&page=1`
        );
        const movieData = await res.json();
        if (res.ok) {
            return{
                props: {movieData}
            };
            
            
        }


    }
</script>

<script>
    export let movieData ;
    import {fly} from 'svelte/transition';
</script>

<div class="movie__data"
  in:fly={{y: 50, duration:500, delay:500}} 
  out:fly={{duration:500}} 
>
    <div class="movie__img">
        <img src={'https://image.tmdb.org/t/p/original' + movieData.backdrop_path} alt={movieData.title}>
    </div>
    <div class="movie__text">
        <h1>{movieData.title}</h1>
        <p class="movie__overview">{movieData.overview}</p>

        <p>
            <span>Release Date:</span>
            {movieData.release_date} <br>

            <span>Budget:</span>
            {movieData.budget} <br>

            <span>Rating:</span>
            {movieData.vote_average}<br>

            <span>Runtime:</span>
            {movieData.runtime}mins <br>
        </p>
    </div>
</div>

<style>
    h1{
        padding: 1rem 0rem 2rem;
    }
    p{
        padding: 1rem 0rem;
    }
    .movie__img{
        width: 100%;
    }
    img{
        width: 100%;
        border-radius:  1rem;
    }
    .movie__text{
        margin: 2rem 20%;
    }
    span{
        font-weight: bold;
    }
</style>
