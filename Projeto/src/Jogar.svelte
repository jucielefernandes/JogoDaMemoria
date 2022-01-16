
<script>
  import VoltarMenu from "./VoltarMenu.svelte";
  import { estado } from "./Estado.js";
  import { trocarEstadoDoJogo } from "./Estado.js";



  class EstadoTabela {
    constructor(limiteVerdadeiros, tabela) {
      this.limiteVerdadeiros = limiteVerdadeiros;
      this.tabela = tabela;
      this.verdadeiros = computarVerdadeiros(tabela);
    }
  }

  

  
  let tabela = [
    ['https://picsum.photos/id/237/536/354', 'https://picsum.photos/id/237/536/354'],
    ['https://picsum.photos/id/237/536/354', 'https://picsum.photos/id/237/536/354'],
    ['https://picsum.photos/id/237/536/354', 'https://picsum.photos/id/237/536/354'],
  ];

  let cartas = [
    ["https://i.picsum.photos/id/44/536/354.jpg?hmac=gr9s90YEHTR2r0xSI_Q-BzX07et5YTXdnM0uRl9gYIc" , "https://i.picsum.photos/id/44/536/354.jpg?hmac=gr9s90YEHTR2r0xSI_Q-BzX07et5YTXdnM0uRl9gYIc"],
    [
      "https://picsum.photos/id/1084/536/354",
      "https://picsum.photos/id/1084/536/354",
    ],
    [
      "https://i.picsum.photos/id/292/536/354.jpg?hmac=JmwZG4JsRmarXfsRwZuzcaOYhm5ZhvdpGAoX6a-syQ0",
      "https://i.picsum.photos/id/292/536/354.jpg?hmac=JmwZG4JsRmarXfsRwZuzcaOYhm5ZhvdpGAoX6a-syQ0",
    ],
  ];


  let emb1 =  cartas[0].sort(() => Math.random() - 0.5)
  
  
 

  let verso = "https://picsum.photos/id/237/536/354";

  let x;
  let y;

  let escolha1;
  let escolha2;

  
  let estadoTabela = new EstadoTabela(6, tabela);


  let pontos = 0;



  
  function computarVerdadeiros(tabela) {
    let verdadeiros=0

    for (let i = 0; i < tabela.length; i++) {
      for (let j = 0; j < tabela.length; j++) {
        if (tabela[i][j]) {
          verdadeiros++;
        }
      }
    }

    return verdadeiros;
  }

  function desflip(x,y,i,j){
    setTimeout(function(){
      
      
      estadoTabela.tabela[i][j] = verso;
      estadoTabela.tabela[x][y] = verso;
    },2000);

    return;

  }

  function reset(){
    escolha1 = null
    escolha2=null
    return;
  }
  
  
  function flip (i,j){
    

      estadoTabela.tabela[i][j] = cartas[i][j];

      if(escolha2==null ){
        x = i;
        y = j
        escolha2=cartas[x][y]
        

      }else if(escolha1==null){
        
        escolha1 = cartas[i][j]
       
      }
      
      
      
      
      
      
      if(escolha1==escolha2 && escolha1!=null && escolha2!=null){

        igual(escolha1,escolha2,x,y,i,j)
      }else if (escolha1!=escolha2 && escolha1!=null && escolha2!=null){

        diferente(escolha1,escolha2,x,y,i,j)
      }
      
  }


  function igual(escolha1,escolha2,x,y,i,j){
    

      if(escolha2===escolha1){
        
        pontos++

        if(pontos==3){
          window.alert("Você venceu")
        }
        reset(escolha1,escolha2)
        
      }
    
  }

  function diferente(escolha1,escolha2, x,y,i,j){
    

     
     
      console.log("diferentes")

     
      reset(escolha1,escolha2)
      desflip(x,y,i,j)
  
  
}

 
  
</script>


<h1>
  Pontos:{pontos} 
</h1>

<table>
  {#each estadoTabela.tabela as linha, i}
    <tr>
      {#each linha as dado, j}
        <td  id={`${i}-${j}`}   on:click={() => flip(i, j)}>
          
          <img src={dado} alt="">
        </td>
      {/each}
    </tr>
  {/each}
</table>

<br />


<VoltarMenu />


