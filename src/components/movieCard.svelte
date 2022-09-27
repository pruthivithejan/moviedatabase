<script>
    export let movie;
</script>


<div class="movie__card">
    <a sveltekit:prefetch sveltekit:noscroll href={'/movie/' + movie.id}>
    <img src={'https://image.tmdb.org/t/p/w500' + movie.poster_path} alt={movie.title} >
    </a>
    <div class="movie__title">
        <h2>{movie.title}</h2>
        <p>{movie.release_date}</p>
    </div>
</div>


<style>
    img{
        width: 100%;
        object-fit: cover;
        border-radius:  1rem;
        margin-bottom:  1.5rem;
    }

    h2{
        font-size:  .9rem;
    }

    .movies__title{
        height: 7vh;
    }

    p{
        font-size: .7rem;
    }
    .movie__card{
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        padding: 1.5rem;
    }
</style>