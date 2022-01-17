<script>
  import VoltarMenu from "./VoltarMenu.svelte";
</script>

<nav class="caixa">
  <div>
    <h1 class="titulo">Como Jogar</h1>
    <h2>
      Escolha duas cartas para desvirá-las. Caso formem um par, seus pontos são
      acrecentados no jogo. Caso contrário as cartas voltam a ficar com as
      figuras voltadas para baixo; O jogo termina quando todos os pares forem
      formados ou a quantidade de erros forem superiores a 10.
    </h2>
  </div>
</nav>

<VoltarMenu  class="v"/>

<style>
  h2 {
    color: aliceblue;
  }

  .caixa {
    width: 300px;
    padding: 25px;
    border: 25px solid navy;
    margin: 25px;
  }
  .v{
	color:#ffae00;
  }
</style>
