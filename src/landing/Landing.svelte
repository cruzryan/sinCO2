<script>
  import { onMount } from "svelte";
  import createGlobe from "cobe";
  import {Link} from "svelte-navigator";

  let logo = "./src/assets/logo.png"

  
  let canvas;
  let phi = 0;

  onMount(() => {
    const globe = createGlobe(canvas.value, {
      devicePixelRatio: 2,
      width: 300 * 2,
      height: 300 * 2,
      phi: 0,
      theta: 0,
      dark: 1,
      diffuse: 1.2,
      mapSamples: 16000,
      mapBrightness: 6,
      baseColor: [0.3, 0.3, 0.3],
      markerColor: [0.5, 1, 1],
      glowColor: [1, 1., 1.4],
      markers: [
        { location: [37.7595, -122.4367], size: 0.03 },
        { location: [40.7128, -74.006], size: 0.1 }
      ],
      onRender: state => {
        state.phi = phi;
        phi += 0.01;
      }
    });
  });
</script>

<main class="App">

  <div class="header">

    <img class="logo" src={logo} alt="background image" />

    <h2>Sobre nosotros</h2>
    <h2>Empleos</h2>
    <h2>Crea una cuenta</h2>

    <button>Inicia Sesión</button>
    
  </div>

  
  <div class="container">
    
    <div class="panel a">

      <h1 class="title">Ayudanos a crear un mundo</h1>
      <img class="logo-big" src={logo} alt="background image" />

      <Link to="comprar">
        <button class="comprar">Comprar Bonos</button>
      </Link>
      <button class="vender">Vender Bonos</button>
      
    </div>
    
    <div class="panel b">
      <canvas bind:this={canvas} style="width: 300px; height: 300px" />
    </div>
  </div>

  
</main>


<style>

  button{
    font-family: 'Raleway', sans-serif !important;
  }
  
  .comprar{
    border: 1px solid #8E8E8E;
    color: #8E8E8E;
    background: white;
    font-size: 15px;
    border-radius: 15px;
    width: 170px;
    height: 30px;
    align-self: center;
    margin-top: 5vh;
    margin-bottom: 5vh;
    cursor: pointer;
  }

  .vender{
    color: #404040;
    border: 0px solid black;
    background-color: white;
    cursor: pointer;
  }

  .container{
    width: 100vw;
    height: 85vh;
    display: flex;
    flex-direction: row;
  }

  .a {
    width: 60%;
    justify-content: flex-start !important;
  }

  .b {
    width: 40%;
  }
  
  .panel{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .header{
    display: flex;
    flex-direction: row;
    height: 15vh;
    width: 100vw;
    justify-content: space-around;
    align-items: center;
  }
  
  .header button{
    border: 1px solid black;
    background-color: white;
    color: black;
    padding: 0.5em 2em;
    border-radius: 15px;
    font-size: 15px;
    font-weight: 900;
    cursor: pointer;
  }
  
  .header h2{
    font-family: 'Raleway', sans-serif !important;
    font-size: 15px;
    color: #8E8E8E;
    font-weight: 500;
    cursor: pointer;
  }

  .header h2:hover{
    color: #727272;
  }
  
  .logo{
    width: 150px;
    height: 40px;
  }

  .logo-big{
    width: 225px;
    height: 60px;
    align-self: center;
  }
    
  
  main{
    background: white;
    color: #fff;
    width: 100vw;
    height: 100vh;

    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;

  }
  
  .title{
    font-size: 30px;
    margin-top: 10vh;
    margin-bottom: 5vh;
  }

  a {
    color: royalblue;
  }
</style>