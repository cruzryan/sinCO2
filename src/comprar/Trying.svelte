<script >
  import {
    Circle,
    Circle2,
    Circle3,
    DoubleBounce,
    GoogleSpin,
    ScaleOut,
    SpinLine,
    Stretch,
    BarLoader,
    Jumper,
    RingLoader,
    SyncLoader,
    Rainbow,
    Wave,
    Firework,
    Pulse,
    Jellyfish,
    Chasing,
    Shadow,
    Square,
    Moon,
    Plane,
    Diamonds,
    Clock
  } from "svelte-loading-spinners";
  export let name;

  let color = "#407C40";
  let size= "60";
  let unit = "px";
  let colorPicker;

  function triggerColorPicker() {
    colorPicker.click();
  }

  import { onMount } from 'svelte';
  onMount(() => {
    setTimeout(function () {
      window.location.href = "/comprar/thanks";
    }, 1000);
	});
</script>

<style>

  main{
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
  }

  .spinner-item {
    min-width: 250px;
    min-height: 250px;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }
  .spinner-title {
    position: absolute;
    bottom: 20px;
  }

  
  
</style>

<main>
<div class="spinner-item" title="Circle">
    <Circle color="#407C40" />
    <div class="spinner-title">Procesando pago...</div>
  </div>
</main>