
<script>
	import VoltarMenu from './VoltarMenu.svelte'
</script>


<nav class="caixa">


<h1 class="titulo">Sobre o jogo</h1>

<h2>Esse jogo foi criado curso Tecnologo em Sistemas para Internet no IFPE campus Igarassu na 
    disciplina Programação Imperativa administrada pelo professor Allan Diego  </h2>

    <h1>Quem fez?</h1>

<ul>
    <li>Adryan</li>
    <li>Daniel</li>
    <li>Magnildo</li>
    <li>Juciele</li>
    <li>Pedro</li>
</ul>

</nav>

<VoltarMenu class="v"/>

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
    img{
        position: flex;
    }
.v{
    color:#ffae00;
}
    </style>