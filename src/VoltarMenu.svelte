<script>
	import { trocarEstadoDoJogo } from './Estado.js'
</script>

<button on:click={() => trocarEstadoDoJogo('menu')}>
	Voltar ao menu
</button>

<style>
	button{
       color:royalblue;
       cursor: pointer;
    }
</style>