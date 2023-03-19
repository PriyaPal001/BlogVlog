<script>
  let tifu = {
    title: "Publish Your Blog ",
    subtitle: "W",
    des: "Write your blog and share it with the world ",
  };
  // @ts-ignore
  import PageHero from "$lib/PageHero.svelte";
  import Stats from "../lib/Stats.svelte";
  import Testimonial from "../lib/Testimonial.svelte";
</script>

<PageHero {tifu} />

<Testimonial />

<Stats />
