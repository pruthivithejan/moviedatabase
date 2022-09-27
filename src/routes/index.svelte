<script context="module">
    
    export async function load({fetch}){
        const API = import.meta.env.VITE_API_KEY;
        const res = await fetch(
            `https://api.themoviedb.org/3/movie/popular?api_key=${API}&language=en-US&page=1`
        );
        const data = await res.json();
        console.log(data);
        if (res.ok) {
            return{
                props: {popular: data.results}
            };
            
            
        }


    }
</script>

<script>
    import PopularMovies from "../components/popularMovies.svelte";
    import Search from '../components/search.svelte';
    import Global from "../css.svelte";
    import {fly} from 'svelte/transition';
    export let popular;
</script>

<section 
  in:fly={{y: 50, duration:500}} 
  out:fly={{duration:500}} 
>
    <Search />
    <PopularMovies {popular}/>
</section>

