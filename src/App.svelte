<script>
  import { onMount } from "svelte";

  // change background
  let body = document.body;
  function updateImageUrl(newUrl) {
    body.style.backgroundImage = `url(${newUrl})`;
    body.style.backgroundSize = "cover";
    body.style.backgroundPosition = "center";
    body.style.backgroundRepeat = "no-repeat";
  }
  updateImageUrl("/images/kokoronashi.png");

  // play song
  let isPlaying = false;
  let audioSource = "/music/kokoronashi.mp3";
  let audio;
  let pause
  onMount(() => {
    window.addEventListener("keydown", (event) => {
      if (event.code === "Space") {
        isPlaying = !isPlaying;
      }
      if (isPlaying) {
        pause.style.display = 'flex'
        audio.play();
      }
      else {
        pause.style.display = 'none'
        audio.pause();
      }
    });
  });
</script>

<main>
  <audio src={audioSource} bind:this={audio}></audio>
  <div bind:this={pause} class="center">
    <h1>pause</h1>
  </div>
</main>

<style>
  .center{
    display: none;
    justify-content: center;
    height: 100vh;
    align-items: center;
  }
</style>
