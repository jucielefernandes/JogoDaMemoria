<svelte:head>
	<link rel="stylesheet" href="public/buiild">
</svelte:head>



<script>
	import { estado } from './Estado.js'
	import { trocarEstadoDoJogo } from './Estado.js'
</script>

<h1 class = "titulo">
    Jogo da memória
</h1>

<button class = "butao" on:click={() => trocarEstadoDoJogo('jogar')}>
	Jogar
</button>

<button on:click={() => trocarEstadoDoJogo('sobre')}>
	Sobre
</button>

<button on:click={() => trocarEstadoDoJogo('ajuda')}>
	Ajuda
</button>


<style>
    h1{
        text-align: center;
        border:solid;
        border-style: double;
        border-color: indigo;
        color:royalblue;
    }

    button{
       color:royalblue;
       cursor: pointer;
       display: flex;
       padding: 10px;
       margin: auto;
    }
</style>