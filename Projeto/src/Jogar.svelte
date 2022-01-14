<script>
  import VoltarMenu from "./VoltarMenu.svelte";
  import { estado } from "./Estado.js";
  import { trocarEstadoDoJogo } from "./Estado.js";

  // Esta classe representa o estado da tela jogar,
  // ela guarda o estado da tabela com trues e false,
  // a quantidade de atual de elementos verdadeiros,
  // e quantidade verdadeiros necessária para ganhar.
  class EstadoTabela {
    constructor(limiteVerdadeiros, tabela) {
      this.limiteVerdadeiros = limiteVerdadeiros;
      this.tabela = tabela;
      this.verdadeiros = computarVerdadeiros(tabela);
    }
  }

  // não seria melhor gerar aleatoriamente?
  let tabela = [
    [false, false],
    [false, false],
    [false, false],
  ];

  let cartas = [
    ["https://picsum.photos/536/354", "https://picsum.photos/536/354"],
    [
      "https://picsum.photos/id/1084/536/354",
      "https://picsum.photos/id/1084/536/354",
    ],
    [
      "https://i.picsum.photos/id/292/536/354.jpg?hmac=JmwZG4JsRmarXfsRwZuzcaOYhm5ZhvdpGAoX6a-syQ0",
      "https://i.picsum.photos/id/292/536/354.jpg?hmac=JmwZG4JsRmarXfsRwZuzcaOYhm5ZhvdpGAoX6a-syQ0",
    ],
  ];

  let verso = "https://picsum.photos/id/237/536/354";

  // toda vez que entramos na tela de jogar o estado do jogo é resetado
  let estadoTabela = new EstadoTabela(6, tabela);

  // não ficaria melhor com POO?
  function computarVerdadeiros(tabela) {
    let verdadeiros = 0;

    for (let i = 0; i < tabela.length; i++) {
      for (let j = 0; j < tabela.length; j++) {
        if (tabela[i][j]) {
          verdadeiros++;
        }
      }
    }

    return verdadeiros;
  }

  // esta função contém a lógica do jogo
  function atualizarTabela(i, j) {
    // atualiza o número de verdadeiros presentes na tabela
    if (estadoTabela.tabela[i][j]) {
      estadoTabela.verdadeiros--;
    } else {
      estadoTabela.verdadeiros++;
    }

    // troca o estado do índice na tabela que o jogador clicou
    // após a execução desta linha, o html da página é reconstruído automáticamente pelo svelte.
    estadoTabela.tabela[i][j] = !estadoTabela.tabela[i][j];

    // testa se a condição de vitória foi atendida
  }
</script>

<svelte:head>
  <link rel="stylesheet" href="/styles/jogar.css" />
</svelte:head>

<!-- notem como utilizamos o '{' e '}' para inserir indicar ao svelte como criar o HTML dinâmicamente -->
<h1>
  Falta trocar {estadoTabela.limiteVerdadeiros - estadoTabela.verdadeiros}
</h1>

<!-- criação da tabela de forma dinâmica, similar aos laços duplos do node que vocês já estão cansados de ver -->
<table>
  {#each estadoTabela.tabela as linha, i}
    <tr>
      {#each linha as dado, j}
        <td on:click={() => atualizarTabela(i, j)}>
          {#if dado == false}
            <img src="https://picsum.photos/id/237/536/354" />
          {:else}
            <img src={cartas[i][j]} />
          {/if}
        </td>
      {/each}
    </tr>
  {/each}
</table>

<br />

<!-- reaproveita o botão de voltar para o menu -->
<VoltarMenu />

<VoltarMenu />
