<script lang="ts">
  import { Parallax, ParallaxLayer } from "svelte-parallax";
  import FadeInOnVisible from "./lib/FadeInOnVisible.svelte";
  import NavBar from "./lib/NavBar.svelte";
  import NavItem from "./lib/NavItem.svelte";

  let parallax;
</script>

<NavBar>
  <h1 slot="title" class="text-white">Title</h1>
  <svelte:fragment slot="items">
    <NavItem on:click={() => parallax.scrollTo(1)}>Home</NavItem>
    <NavItem on:click={() => parallax.scrollTo(2)}>Price</NavItem>
    <NavItem on:click={() => parallax.scrollTo(3)}>About</NavItem>
  </svelte:fragment>
</NavBar>

<Parallax bind:this={parallax} sections={2.5} class="bg-black">
  <ParallaxLayer
    rate={-0.3}
    span={1}
    class="bg-blue-500 bg-[url('https://images.pexels.com/photos/2400594/pexels-photo-2400594.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2')]"
  />
  <ParallaxLayer rate={0} span={1}>
    <div class="container flex h-full items-center">
      <FadeInOnVisible>
        <h1 class="text-[4rem] font-extrabold leading-none text-white">
          Lorem <br /> dolor sit
        </h1>
        <p class="mt-4 max-w-[500px] text-white">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum iusto odit fugiat
          praesentium blanditiis. Esse possimus obcaecati eveniet autem temporibus.
        </p>
      </FadeInOnVisible>
    </div>
  </ParallaxLayer>

  <ParallaxLayer rate={0} offset={1} span={1} class="bg-orange-500">
    <div class="container flex h-full items-center">
      <FadeInOnVisible class="sm:grid sm:grid-cols-2">
        <h1 class="text-[4rem]">Price</h1>
        <p class="border-l border-black pl-2">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nemo modi quas totam, dolorem
          aut accusamus. Dolorum sequi iste sapiente explicabo.
        </p>
      </FadeInOnVisible>
    </div>
  </ParallaxLayer>

  <ParallaxLayer rate={0} offset={2} span={0.5} class="bg-gray-700">
    <div class="container flex h-full items-center text-white">
      <ul class="grid w-full grid-cols-2 gap-4">
        <li>sponsor</li>
        <li>sponsor</li>
        <li>sponsor</li>
        <li>sponsor</li>
        <li>sponsor</li>
        <li>sponsor</li>
      </ul>
    </div>
  </ParallaxLayer>
</Parallax>
