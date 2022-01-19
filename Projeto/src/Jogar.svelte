<script>
  import VoltarMenu from "./VoltarMenu.svelte";


  class EstadoTabela {
    constructor(limiteVerdadeiros, tabela) {
      this.limiteVerdadeiros = limiteVerdadeiros;
      this.tabela = tabela;
      this.verdadeiros = computarVerdadeiros(tabela);
    }
  }

  let tabela = [
    [
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
    ],
    [
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
    ],
    [
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
      "https://picsum.photos/id/237/536/354",
    ],
  ];

  let cartas = [
    [
      "https://i.picsum.photos/id/292/536/354.jpg?hmac=JmwZG4JsRmarXfsRwZuzcaOYhm5ZhvdpGAoX6a-syQ0",
      "https://i.picsum.photos/id/44/536/354.jpg?hmac=gr9s90YEHTR2r0xSI_Q-BzX07et5YTXdnM0uRl9gYIc",
      "https://i.picsum.photos/id/866/536/354.jpg?hmac=tGofDTV7tl2rprappPzKFiZ9vDh5MKj39oa2D--gqhA",
      "https://i.picsum.photos/id/1060/536/354.jpg?blur=2&hmac=0zJLs1ar00sBbW5Ahd_4zA6pgZqCVavwuHToO6VtcYY",
    ],
    [
      "https://i.picsum.photos/id/292/536/354.jpg?hmac=JmwZG4JsRmarXfsRwZuzcaOYhm5ZhvdpGAoX6a-syQ0",
      "https://picsum.photos/id/1084/536/354",
      "https://i.picsum.photos/id/1060/536/354.jpg?blur=2&hmac=0zJLs1ar00sBbW5Ahd_4zA6pgZqCVavwuHToO6VtcYY",
      "https://i.picsum.photos/id/870/536/354.jpg?blur=2&grayscale&hmac=A5T7lnprlMMlQ18KQcVMi3b7Bwa1Qq5YJFp8LSudZ84",
    ],
    [
      "https://picsum.photos/id/1084/536/354",
      "https://i.picsum.photos/id/44/536/354.jpg?hmac=gr9s90YEHTR2r0xSI_Q-BzX07et5YTXdnM0uRl9gYIc",
      "https://i.picsum.photos/id/866/536/354.jpg?hmac=tGofDTV7tl2rprappPzKFiZ9vDh5MKj39oa2D--gqhA",
      "https://i.picsum.photos/id/870/536/354.jpg?blur=2&grayscale&hmac=A5T7lnprlMMlQ18KQcVMi3b7Bwa1Qq5YJFp8LSudZ84",
    ],
  ];

  let verso = "https://picsum.photos/id/237/536/354";

  let x;
  let y;

  let escolha1;
  let escolha2;

  let estadoTabela = new EstadoTabela(6, tabela);

  let pontos = 0;
  let erros = 0;

  function shuffle(array) {
    let currentIndex = array.length,
      randomIndex;

    while (currentIndex != 0) {
      randomIndex = Math.floor(Math.random() * currentIndex);
      currentIndex--;

      [array[currentIndex], array[randomIndex]] = [
        array[randomIndex],
        array[currentIndex],
      ];
    }

    return array;

    //Função de embaralhar array:https://stackoverflow.com/questions/2450954/how-to-randomize-shuffle-a-javascript-array
  }

  cartas = [shuffle(cartas[0]), shuffle(cartas[1]), shuffle(cartas[2])];
  cartas = shuffle(cartas);

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

  function desflip(x, y, i, j) {
    setTimeout(function () {
      estadoTabela.tabela[i][j] = verso;
      estadoTabela.tabela[x][y] = verso;
    }, 1000);

    return;
  }

  function reset() {
    escolha1 = null;
    escolha2 = null;

    return;
  }

  function flip(i, j) {
    estadoTabela.tabela[i][j] = cartas[i][j];

    if (escolha2 == null) {
      x = i;
      y = j;
      escolha2 = cartas[x][y];
    } else if (escolha1 == null) {
      escolha1 = cartas[i][j];
    }

    if (escolha1 == escolha2 && escolha1 != null && escolha2 != null) {
      igual(escolha1, escolha2, x, y, i, j);
    } else if (escolha1 != escolha2 && escolha1 != null && escolha2 != null) {
      diferente(escolha1, escolha2, x, y, i, j);
    }
  }

  function igual(escolha1, escolha2) {
    if (escolha2 === escolha1) {
      reset(escolha1, escolha2);
      pontos++;
      if (pontos == 6) {
        alert("Você venceu");

        document.location.reload(true); // Reiniciar encontrado: https://developer.mozilla.org/pt-BR/docs/Web/API/Location/reload
      }
    }
  }

  function diferente(escolha1, escolha2, x, y, i, j) {
    reset(escolha1, escolha2);
    desflip(x, y, i, j);
    erros++;
    if (erros == 10) {
      alert("Você perdeu");
      document.location.reload(true);
    }
  }
</script>

<h1>
  Pontos:{pontos}
</h1>

<h1>Erros:{erros}</h1>
<div class="caixa">
  <table>
    {#each estadoTabela.tabela as linha, i}
      <tr>
        {#each linha as dado, j}
          <td id={`${i}-${j}`} on:click={() => flip(i, j)}>
            <img src={dado} alt="" />
          </td>
        {/each}
      </tr>
    {/each}
  </table>
</div>
<br />

<VoltarMenu />

<style>

  img {
    transition: 2s;
    cursor: pointer;
    border: 10px solid white;
  }

  img:hover {
    transform: scale(1.1);
  }

  .caixa{
  display: flex;
	justify-content: center;
  }
</style>
