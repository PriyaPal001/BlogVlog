<script>
  import { onMount } from "svelte";
  let tifu = {
    title: "Publish Your Blog ",
    subtitle: "W",
    des: "Write your blog and share it with the world ",
  };
  // @ts-ignore
  import PageHero from "$lib/PageHero.svelte";
  import Stats from "../lib/Stats.svelte";
  // @ts-ignore
  import Testimonial from "../lib/Testimonial.svelte";
  import AOS from "aos";
  import "aos/dist/aos.css"; // You can also use <link> for styles
  // ..
  onMount(() => {
    AOS.init();
  });
</script>

<PageHero {tifu} />

<Testimonial />

<Stats />

