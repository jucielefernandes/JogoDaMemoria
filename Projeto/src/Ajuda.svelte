<script>
  import VoltarMenu from "./VoltarMenu.svelte";
</script>

<div class="centralizar">
<nav class="caixa">
  <div>
    <h1 class="titulo">Como Jogar</h1>
    <h2>
      Escolha duas cartas para desvirá-las. Caso formem um par, seus pontos são
      acrecentados no jogo. Caso contrário as cartas voltam a ficar com as
      figuras voltadas para baixo; O jogo termina quando todos os pares forem
      formados ou a quantidade de erros forem iguais a 10.
    </h2>
  </div>
</nav>
</div>

<VoltarMenu/>

<style>
  h2 {
    color: aliceblue;
  }

  .caixa {
    width: 300px;
    padding: 25px;
    border: 10px solid white;
    margin: 25px;
  }
  .centralizar{
    display: flex;
	justify-content: center;
  }
</style>
