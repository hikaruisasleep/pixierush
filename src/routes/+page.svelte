<script lang="ts">
  import pixiepad from "$lib/pixiepad.png";
  import bg_pixelcity_vp9 from "$lib/bg-pixelcity-vp9.webm";
  import bg_pixelcity_av1 from "$lib/bg-pixelcity-av1.webm";
  import { onMount } from "svelte";

  function report() {
    console.log(`mask ${maskStates}`);
  }

  let maskStates: [number, boolean] = $state([0, true]);

  function switchMasks() {
    if (maskStates[1] == true) {
      maskStates[1] = false;
    } else {
      if (maskStates[0] >= 2) {
        maskStates[0] = 0;
      } else {
        maskStates[0] = maskStates[0] + 1;
      }
      maskStates[1] = true;
    }
  }

  onMount(() => {
    const interval = setInterval(() => switchMasks(), 2000);
    return () => {
      clearInterval(interval);
    };
  });
</script>

<div class="min-h-screen md:max-w-md max-w-screen flex flex-col flex-0 mx-auto">
  <header class="w-full py-4 px-12 h-24 md:h-18 flex flex-row justify-center shadow-gray-400 shadow-md fixed top-0 right-0 left-0 bg-white z-[1]">
    <div class="logo flex flex-col items-center justify-center gap-1">
      <div class="max-w-16 md:max-w-10">
        <img src={pixiepad} alt="pixierush logo" />
      </div>
      <h1 class="text-lg md:text-xs">pIxIerush.Id</h1>
    </div>
  </header>

  <nav class="nav flex flex-row items-center justify-around gap-1 hidden">
    <a href="">home</a>
    <a href="">about</a>
    <a href="">about</a>
  </nav>

  <div class="h-screen w-full py-10 flex flex-col items-center justify-center relative">
    <video autoplay muted loop playsinline class="fixed top-0 -z-50 h-full w-full md:w-md object-cover">
      <source src={bg_pixelcity_av1} type="video/webm" />
      <source src={bg_pixelcity_vp9} type="video/webm" />
    </video>
    <div class="bg-gradient-to-b from-transparent from-0% via-white/50 via-50% to-transparent to-100% w-full h-1/2 flex flex-col justify-center items-center">
      <h2 class="w-full text-fulfill leading-none inline-block px-2 select-none">
        <span
          ><span>
            Your gaming<br />
            <span class="text-[#cb1643] bg-white absolute" class:hidden={maskStates[0] != 0} class:mask-item-in={maskStates[1]} class:mask-item-out={!maskStates[1]}>
              friend.
            </span>
            <span class="text-[#cb1643] bg-white absolute" class:hidden={maskStates[0] != 1} class:mask-item-in={maskStates[1]} class:mask-item-out={!maskStates[1]}>
              curator.
            </span>
            <span class="text-[#cb1643] bg-white absolute" class:hidden={maskStates[0] != 2} class:mask-item-in={maskStates[1]} class:mask-item-out={!maskStates[1]}>
              companion.
            </span>
          </span></span
        >
        <span aria-hidden="true">Your gaming<br />companion.</span>
      </h2>
      <p class="text-white font-[NHAAS] tracking-wider relative top-54">recommendations, reviews, and more</p>
    </div>

    <div class="absolute bottom-12">
      <span class="text-white static text-2xl">
        <i class="fa-solid fa-chevron-down absolute bottom-2 -left-[0.9ch]"></i>
        <i class="fa-solid fa-chevron-down absolute bottom-0 -left-[0.9ch]"></i>
      </span>
    </div>
  </div>

  <div class="h-screen flex flex-col bg-black text-white px-4 justify-center">
    <div class="h-24 md:h-18"></div>
    <div class="flex flex-row justify-between items-center gap-8 grow">
      <h3 class="leading-none px-2 select-none w-2/3 text-fulfill font-[MultiType_Pixel]">
        <span><span>recommendations</span></span>
        <span aria-hidden="true">recommendations</span>
      </h3>
      <p class="w-1/3 text-right">Temukan game baru untuk dimainkan saat santai, baik sendiri maupun bersama teman.</p>
    </div>
    <div class="flex flex-row-reverse justify-between items-center gap-8 grow">
      <h3 class="leading-none select-none w-1/3 text-fulfill font-[MultiType_Pixel]">
        <span><span> rEvIEws </span></span>
        <span aria-hidden="true">reviews</span>
      </h3>
      <p class="w-2/3 text-left">Lihat jika game incaranmu benar-benar sesuai harapanmu.</p>
    </div>
    <div class="flex flex-row justify-between items-center gap-8 grow">
      <h3 class="leading-none px-2 select-none w-1/3 text-fulfill font-[MultiType_Pixel]">
        <span><span>updates</span></span>
        <span aria-hidden="true">updates</span>
      </h3>
      <p class="w-2/3 text-right">Dapatkan informasi terbaru seputar dunia gaming.</p>
    </div>
  </div>
</div>

<style>
  .mask-item-in {
    animation: mask-in 2s ease 1 normal;
    animation-fill-mode: backwards;
  }

  .mask-item-out {
    animation: mask-out 2s ease 1 normal;
    animation-fill-mode: forwards;
  }

  @keyframes mask-in {
    0% {
      mask: linear-gradient(90deg, #000 50%, #0000 0) content-box 100% 100% / 200% 200% no-repeat;
    }
    100% {
      mask: linear-gradient(90deg, #000 50%, #0000 0) content-box 0% 0% / 200% 200% no-repeat;
    }
  }

  @keyframes mask-out {
    0% {
      mask: linear-gradient(270deg, #000 50%, #0000 0) content-box 100% 100% / 200% 200% no-repeat;
    }
    100% {
      mask: linear-gradient(270deg, #000 50%, #0000 0) content-box 0% 0% / 200% 200% no-repeat;
    }
  }
</style>
