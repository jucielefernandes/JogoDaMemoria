<script>
  import VoltarMenu from "./VoltarMenu.svelte";
</script>

<div class="centralizar">
<nav class="caixa">
  <h1 class="titulo">Sobre o jogo</h1>

  <h2>
    Esse jogo foi criado curso Tecnologo em Sistemas para Internet no IFPE
    campus Igarassu na disciplina Programação Imperativa administrada pelo
    professor Allan Diego
  </h2>

  <h1>Quem fez?</h1>

  <ul>
    <li>Adryan</li>
    <li>Daniel</li>
    <li>Magnildo</li>
    <li>Juciele</li>
    <li>Pedro</li>
  </ul>
</nav>
</div>
<VoltarMenu />

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
