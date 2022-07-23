<script>
  import {Link} from "svelte-navigator";
  
  let forest = "./src/assets/forest.png";
  let bookmark = "./src/assets/bookmark.png";
  let share = "./src/assets/share.png";
  
  import data from "/data.json"
  import { onMount } from 'svelte';

  let buscarspace = []

  let us = ["54 Ranch", "A-Gas 1-2021", "Reclamation Technologies Inc.", "Wood County, Bowling Green", "A-Gas 4-2020", "Bowling Green", "A-Gas O'Hare", "A-GAS RemTec 2014-1", "A-Gas UCSD1", "Adirondack Farms",  "AgriCapture Soil Enrichment #1", "AgriCapture Soil Enrichment #2", "Alder Stream Preserve"]

let mx = ["Alhuajoyucan", "Acaxochitlan", "San Pedro Ecatzingo", "Santa Isabel Chalma", "Amecameca", "Santiago Cuautenco", "CO2-El Naranjal",  "CO2-San Antonio Tuk", "CO2_San Felipe Oriente"]
  
  onMount(async () => {
    console.log("lele")
    console.log("DATA: ", data)
    redocalc(us)
	});


  let mapToggle = "Area";
  let regionToggle = "US";
  let rightToggle = 0;

  function changeRight(k){
    rightToggle = k

    if(k == 2){
      let shuffled = buscarspace
  .map(value => ({ value, sort: Math.random() }))
  .sort((a, b) => a.sort - b.sort)
  .map(({ value }) => value)

      for(var i = 0; i < shuffled.length; i++){
        shuffled[i].price = `${randomIntFromInterval(1,28)}/${randomIntFromInterval(1,4)}/2022`
      }
      buscarspace = shuffled
    }
  }
  
  function changeMap(){
    if (mapToggle == "Area"){
      mapToggle = "Tipo";
    }else{
      mapToggle = "Area";
    }
  }
  function randomIntFromInterval(min, max) {
    return Math.floor(Math.random() * (max - min + 1) + min)
  }
  
  function redocalc(names){
    buscarspace = []
    for(var i = 0; i<names.length; i++){
      buscarspace.push({
        place: names[i],
        price: `$${90+ randomIntFromInterval(4,23)} MXN`,
        area: 30000 + randomIntFromInterval(2222,19123),
        carbon: 59147 + randomIntFromInterval(2222,49123)
      })
    }
      
  }
  function changeRegion(){
    if (regionToggle == "US"){
      redocalc(mx);
      regionToggle = "MX";
    }else{
      redocalc(us);
      regionToggle = "US";
    }
  }
</script>

<main>
  <div class="subbard">
    <div class="toggly2">
      <h1 on:click={() => changeRegion()} 
        class='{regionToggle == "US"? "toggly2-toggled" : ""}'>US</h1>
      <h1 on:click={() => changeRegion()} class='{regionToggle == "MX"? "toggly2-toggled" : ""}'>MX</h1>
    </div>

    <div class="search">
      <input class="searchin" type="text" placeholder="Buscar..."/>
    </div>

    <div class="icons">

      <div>
        <svg xmlns="http://www.w3.org/2000/svg" className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
  <path strokeLinecap="round" strokeLinejoin="round" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
</svg>
      </div>
      
      <div>
      <svg xmlns="http://www.w3.org/2000/svg" className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="#30293A" strokeWidth={2}>
  <path strokeLinecap="round" strokeLinejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM10 7v3m0 0v3m0-3h3m-3 0H7" />
</svg>
      </div>

    <div>
      <svg xmlns="http://www.w3.org/2000/svg" className="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="#30293A" strokeWidth={2}>
  <path strokeLinecap="round" strokeLinejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0zM13 10H7" />
</svg>
    </div>
    
    </div>

    
  </div>

  <div class="toggly">
    <div class="division">
      <h1 on:click={() => changeMap()} class='{mapToggle == "Area"? "toggled" : ""}' >Area</h1>
    </div>
    <div class="division">
      <h1 on:click={() => changeMap()} class='{mapToggle == "Tipo"? "toggled" : ""}' >Tipo de arbol</h1>
    </div>
  </div>
  
  <div class="container">
    <div class="panel a">
      <img class="fimg" src={forest} alt="Image of a forest"/>

    <div class="infos">
      <div class="info">
        <div class="suba">
          <h1 class="info-title">Sierra Gorda</h1>
          <h2 class="info-desc">Lugar</h2>
        </div>
      </div>

      <div class="info">
        <div class="suba">
          <h1 class="info-title">120</h1>
          <h2 class="info-desc">Costo</h2>
        </div>
        <div class="subb">
          <h1>MXN</h1>
        </div>
      </div>

      <div class="info">
        <div class="suba">
          <h1 class="info-title">40,000</h1>
          <h2 class="info-desc">Area</h2>
        </div>
        <div class="subb">
          <h1>km2</h1>
        </div>
      </div>

      <div class="info">
        <div class="suba">
          <h1 class="info-title">59,147</h1>
          <h2 class="info-desc">Carbón reducido</h2>
        </div>
        <div class="subb">
          <h1>Toneladas</h1>
        </div>
      </div>

    <Link to="processing">
      <button class="buy">Comprar</button>
    </Link>
    </div>

    <div class="container-2">
      <p class="paragraph">
        Somos una comunidad indigena que se enfoca en cuidar el ambiente, en especifico la zona de la Sierra Gorda, esta zona ha sido cuidada y preservada por nuestra comunidad desde hace 1922, y hemos crecido la flora y la fauna dentro de esta por ya varios años.
      </p>
    </div>
    </div>
    <div class="panel b">

      <div class="toppy">
        <h1 on:click={() => changeRight(0)} class='{rightToggle == 0? "toppy-selected" : ""}'>Buscar</h1>
        <h1 on:click={() => changeRight(1)} class='{rightToggle == 1? "toppy-selected" : ""}'>Ordenes pasadas</h1>
        <h1 on:click={() => changeRight(2)} class='{rightToggle == 2? "toppy-selected" : ""}'>Actualizaciones</h1>
      </div> 

      <div class="listy">
        {#each buscarspace as _, i}
        <div class="enti">
          <div class="entilist">
            <h1>{buscarspace[i].place}</h1>
            <h2>{buscarspace[i].price}</h2>
          </div>
          {#if rightToggle != 2}
          <div class="entibtns">
            <img src={bookmark} alt="bookmark"/>
            <img src={share} alt="share"/>
          </div>
        {/if}
        </div>
        {/each}

        
      </div>
    </div>
  </div>
</main>

<style>

  .icons{
    display: flex;
    flex-direction: row;
    margin-left: 12vw;
    cursor: pointer;
  }

  .icons > div{
    width: 20px;
    height: 20px;
    margin-left: 15px;
  }
  
  .entibtns{
    margin-left: 4em;
  }
  
  .entibtns img{
    margin-left: 1em;
  }

  .listy{
    display: flex;
    flex-direction: column;
    margin-top: 5vh;
    max-height: 100vh;
    width: 30vw;
    overflow-y: scroll;
  }

  .enti{
    display: flex;
    flex-direction: row;
    padding-top: 2em;
    padding-bottom: 2em;
    cursor: pointer;
    width: 30vw;
  }
  
  .enti:hover{
    background-color: #F2F2F2;
  }
  
  .enti h1{
    color: #4B4B4B;
    font-weight: 300;
    font-size: 20px;
    padding-left: 3vw;
  }

  .enti h2{
    color: #B8D3BE;
    font-size: 15px;
    padding-left: 5%;
    padding-left: 3vw;    
  }
    
  .toppy-selected{
    font-weight: bold;
    color: black !important;
  }

  .toppy{
    display: flex;
    flex-direction: row;
    width: 30vw;
    justify-content: space-evenly;
    margin-top: 5vh;
    cursor: pointer;
  }

  .toppy h1{
    font-size: 15px;
    font-weight: 500;
    color: #C3C6CB;
  }

  .searchin{
    color: #C3C6CB;
    border: 1px solid #C3C6CB;
    border-radius: 5px;
    width: 30vw;
    padding: 0.5em;
    margin-left: 1vw;
  }
  
  .search{
    display: flex; 
    flex-direction: row;
  }


  .sl{
    color: black;
  }

  input:focus{
    outline: none;
  }
  
  .buy{
    font-size: 20px;
    border-radius: 5px;
    background-color: black;
    font-weight: 500;
    padding: 0.1em 1.5em;
    margin-left: 5%;    
    color: white;
    cursor: pointer;
  }
  
  .toggly2-toggled{
    background-color: #F2F2F2;
    border-radius: 5px;
    font-weight: 900;

  }

  .toggly2 h1{
    font-size: 15px;
    padding-left: 0.5em;
    padding-right: 0.5em;
    margin-top: 5%;
    font-weight: 300;
    cursor: pointer;
  }
  
  .toggly2{
    display: flex; 
    flex-direction: row;
    margin-left: 1vw;
    align-items: center;
    
  }
  
  .subbard{
    position: absolute;
    display: flex;
    flex-direction: row;
    background-color: white;
    align-items: center;
    width: 60vw;
    height: 7vh;
    margin-left: 5vw;
    border-radius: 5px;
    margin-top: 40vh;
  }
  

  .container-2{
    width: 100%;
  }

  .paragraph{
    width: 40%;
    margin-left: 7%;
    margin-top: 5vh;
  }
  
  .toggly{
    position: absolute;
    flex-direction: row;
    justify-content: center;
    background-color: white;
    z-index: 2;
    display: flex;
    flex-direction: row;
    align-items: center;
    width: 12vw;
    height: 7vh;
    border-radius: 5px;
    margin-top: 5vh;
    margin-left: 55vw;
  }

  .division h1{
    font-size: 12px;
    font-weight: 500;
    font-family: 'Raleway', sans-serif !important;
    padding: 0.6em;
    cursor: pointer;
  }

  .toggled{
    background-color: #F2F2F2;
    border-radius: 5px;
    font-size: 15px;
    align-items: center;
    font-weight: 900;
  }
  
  .infos{
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  .subb h1{
    font-size: 12px;  
  } 
  
  .suba{
    display: flex;
    flex-direction: column;
  }

  .info{
    display: flex;
    flex-direction: row;
    margin-left: 5vw;
    margin-top: 5vh;
  }

  .info-title{
    color: #414141;
  }

  .info-desc{
    color: #808080;
  }
  
  .container{
    display: flex;
    flex-direction: row;
    width: 100vw;
    height: 100vh;
  }

  .panel{
    display: flex;
    flex-direction: column;
  }

  .fimg{
    width: 70vw;
    height: 55vh;
    object-fit: cover;
  }
  
  .a{
    width: 70vw;
    height: 100vh;
  }

  .b{
    width: 20vw;
    height: 100vh;
  }

  
</style>