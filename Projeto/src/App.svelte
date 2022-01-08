<script>

	import Jogo from './Jogar.svelte'
	import Sobre from './Sobre.svelte'
	import Menu from './Menu.svelte'
	import { estado } from './Estado.js'
	import Ajuda from './Ajuda.svelte'
</script>

 

{#if $estado === 'menu'}
	<Menu/>
{:else if $estado === 'sobre'}
	<Sobre/>
{:else if $estado === 'jogar'}
	<Jogo/>
{:else if $estado === 'ajuda'}
	<Ajuda/>
{/if}