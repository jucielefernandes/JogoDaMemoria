<script>
	import { trocarEstadoDoJogo } from './Estado.js'
</script>


<div class="botoes">
    <button class="botoes" on:click={() => trocarEstadoDoJogo('menu')}>
        Voltar ao menu
    </button>
</div>

<style>
    div.botoes{
      align-items: center;
      margin: 100px ;
    }
   
    button{
      border-radius: 0.6em;
    border-color: royalblue;
    color: #fff;
    background-image: -webkit-linear-gradient(left, rgb(0, 64, 131), rgb(0, 64, 131) 5%, #0074bd 5%, #0074bd 10%, rgb(0, 64, 131) 10%, rgb(0, 64, 131) 15%, #0074bd 15%, #0074bd 20%, rgb(0, 64, 131) 20%, rgb(0, 64, 131) 25%, #0074bd 25%, #0074bd 30%, rgb(0, 64, 131) 30%, rgb(0, 64, 131) 35%, #0074bd 35%, #0074bd 40%, rgb(0, 64, 131) 40%, rgb(0, 64, 131) 45%, #0074bd 45%, #0074bd 50%, rgb(0, 64, 131) 50%, rgb(0, 64, 131) 55%, #0074bd 55%, #0074bd 60%, rgb(0, 64, 131) 60%, rgb(0, 64, 131) 65%, #0074bd 65%, #0074bd 70%, rgb(0, 64, 131) 70%, rgb(0, 64, 131) 75%, #0074bd 75%, #0074bd 80%, rgb(0, 64, 131) 80%, rgb(0, 64, 131) 85%, #0074bd 85%, #0074bd 90%, rgb(0, 64, 131) 90%, rgb(0, 64, 131) 95%, #0074bd 95%, #0074bd 100%);
    background-image: linear-gradient(to right, rgb(0, 64, 131), rgb(0, 64, 131) 5%, #0074bd 5%, #0074bd 10%, rgb(0, 64, 131) 10%, rgb(0, 64, 131) 15%, #0074bd 15%, #0074bd 20%, rgb(0, 64, 131) 20%, rgb(0, 64, 131) 25%, #0074bd 25%, #0074bd 30%, rgb(0, 64, 131) 30%, rgb(0, 64, 131) 35%, #0074bd 35%, #0074bd 40%, rgb(0, 64, 131) 40%, rgb(0, 64, 131) 45%, #0074bd 45%, #0074bd 50%, rgb(0, 64, 131) 50%, rgb(0, 64, 131) 55%, #0074bd 55%, #0074bd 60%, rgb(0, 64, 131) 60%, rgb(0, 64, 131) 65%, #0074bd 65%, #0074bd 70%, rgb(0, 64, 131) 70%, rgb(0, 64, 131) 75%, #0074bd 75%, #0074bd 80%, rgb(0, 64, 131) 80%, rgb(0, 64, 131) 85%, #0074bd 85%, #0074bd 90%, rgb(0, 64, 131) 90%, rgb(0, 64, 131) 95%, #0074bd 95%, #0074bd 100%);
    background-position: 0 0;
    background-size: 100%;
    -webkit-transition: background 300ms ease-in-out;
    transition: background 300ms ease-in-out;
    display: flex;
    padding: 30px;
    margin: auto;
    transition: all .5s;
    

    }
  button:hover {
    background-position: 100px;
    border-radius: 20%;
    border: 10px solid white;
  }
  </style>