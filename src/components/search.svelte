<script>
    let inputValue = '';
    let active = false ;
    import {goto} from "$app/navigation";
    import {fly} from 'svelte/transition';

    function cancelInactive(){
        if (inputValue){
            active = true
        } else {
            active = false
        }

    }

    function submitSearch(){
       goto("/search/"+ inputValue);
    }
</script>

<form on:submit|preventDefault={submitSearch} class="search">
    {#if !active}
     <label 
        in:fly={{y: -10, duration:500}} 
        out:fly={{y: -10, duration:500}} 
     for="search__movie">Search Movie</label> 
    {/if}
    
    <input 
       on:blur={cancelInactive} 
       on:focus={() => (active = true)} 
       bind:value={inputValue} 
       type="text" name="search__movie"
       class={active ? 'selected' : ''}>

    {#if inputValue}
    <button
      in:fly={{x: 20, duration:500}} 
      out:fly={{x: 0, duration:500}}
    >Search</button>
    {/if}
 
</form>

<style>
    .search{
       position: relative;
       width: 30%;
       margin: 1rem;
    }
    button{
        font-size: .8rem;
        padding: 0rem 1.5rem;
        background: rgb(96, 110, 201);
        color: white;
        font-weight: bold;
        border: none;
        position: absolute;
        bottom: 50%;
        right: -14%;
        transform: translate(0, 50%);
        height: 100%;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        cursor: pointer;
        font-family: 'Poppins', sans-serif;
    }
    input{
        width: 100%;
        border: none;
        outline: none;
        color: rgb(255, 255, 255);
        padding: .5rem .1rem;
        transition: backgroud 0.75s ease-out;
        font-weight:  bold;
        background: rgb(63, 63, 63);
        border-radius: 10px;
        padding: 1rem;
    }
    label{
        opacity: 60%;
        font-family: 'Poppins', sans-serif;
        position: absolute;
        font-size: .8rem;
        top: 50%;
        left: 0;
        transform: translate(0, -50%);
        color: #fff;
        padding: 0rem 1rem;
    }
    input.selected{
        background: rgb(50, 50, 50) ;
    }

</style>