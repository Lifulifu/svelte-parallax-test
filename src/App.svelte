<script>
  import { Parallax, ParallaxLayer } from "svelte-parallax";
  import FadeInOnVisible from "./lib/FadeInOnVisible.svelte";

  let parallax;
</script>

<nav class="fixed top-0 z-50 w-full bg-black/50">
  <div class="container-3xl flex items-center py-4 text-white">
    <h1 class="mr-auto text-xl">LIFU</h1>
    <ul class="flex w-full justify-end gap-6">
      <li><button on:click={() => parallax.scrollTo(1)}>Home</button></li>
      <li><button on:click={() => parallax.scrollTo(2)}>Price</button></li>
      <li><button on:click={() => parallax.scrollTo(3)}>About</button></li>
    </ul>
  </div>
</nav>

<Parallax bind:this={parallax} sections={3}>
  <ParallaxLayer
    rate={-0.3}
    span={1}
    class="bg-blue-500 bg-[url('https://images.pexels.com/photos/2400594/pexels-photo-2400594.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2')]"
  />
  <ParallaxLayer rate={0} span={1}>
    <div class="container-3xl flex h-full items-center">
      <FadeInOnVisible>
        <h1 class="text-[4rem] font-extrabold leading-none text-white">
          Lorem <br /> dolor sit
        </h1>
        <p class="mt-4 text-white">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum iusto odit fugiat
          praesentium blanditiis. Esse possimus obcaecati eveniet autem temporibus.
        </p>
      </FadeInOnVisible>
    </div>
  </ParallaxLayer>

  <ParallaxLayer rate={0} offset={1} span={1} class="bg-orange-500">
    <div class="container-3xl flex h-full items-center">
      <FadeInOnVisible class="sm:grid sm:grid-cols-2">
        <h1 class="text-[4rem]">Price</h1>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nemo modi quas totam, dolorem
          aut accusamus. Dolorum sequi iste sapiente explicabo.
        </p>
      </FadeInOnVisible>
    </div>
  </ParallaxLayer>
</Parallax>
