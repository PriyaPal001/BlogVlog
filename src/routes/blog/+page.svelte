<script>
  // @ts-nocheck
  import { fufi } from "../../store";
  import supabase from "$lib/db";
  import { onMount } from "svelte";

  let studProData = [
    {
      title: "Rahul Wagh",
      img: "https://i.pinimg.com/564x/34/ac/14/34ac14141d8a9811a651c50e23aef2d4.jpg",
      projName: "VC Funders",
    },
    {
      title: "Aditya Karle",
      img: "https://i.pinimg.com/564x/63/6a/09/636a09d9c32d34f9b4037e1fac5db6cf.jpg",
      projName: "City-Scape AR",
    },
    {
      title: "Priya Pal",
      img: "https://i.pinimg.com/564x/ad/ba/6d/adba6d6b6f7192aaf60f50372f00b9d8.jpg",
      projName: "Dream Dress",
    },
    {
      title: "Saloni Maheshwari",
      img: "https://i.pinimg.com/564x/57/3c/af/573cafd440c1dd21f462ff7339ccaa19.jpg",
      projName: "Mumbai Drvizzz",
    },
    {
      title: "Rutika Bhuimbar",
      img: "https://i.pinimg.com/564x/f3/68/ac/f368aca0fe4f7bb47c982a1bf1062e2b.jpg",
      projName: "Realz Lifo",
    },
    {
      title: "Kuldeep Jha",
      img: "https://i.pinimg.com/564x/0a/86/9a/0a869a26132aa2982c57b958e71d80b9.jpg",
      projName: "Kool-Berg ",
    },
    {
      title: "Abhishek Gopale",
      img: "https://i.pinimg.com/564x/0a/c3/f6/0ac3f68e2c8b88489400978f98c3c77d.jpg",
      projName: "Defi - Sefi",
    },
    {
      title: "Roshan John",
      img: "https://i.pinimg.com/564x/4d/7f/24/4d7f24025c9f964960747da8a64d8ceb.jpg",
      projName: "Fuse Flicker",
    },
    {
      title: "Yash Kulkarni",
      img: "https://i.pinimg.com/564x/05/de/31/05de315a05b6b81880ca5aefdeac762e.jpg",
      projName: "Ctiy Lights",
    },
    {
      title: "Raj Setti",
      img: "https://i.pinimg.com/564x/af/69/ab/af69ab11f4525ccc68d07a9ef0ccb589.jpg",
      projName: "Vision Latent",
    },
    {
      title: "Naman Gupta",
      img: "https://i.pinimg.com/564x/be/8d/18/be8d1804bb1ffd71e8aef9ea37540cb5.jpg",
      projName: "Prico Velas",
    },
    {
      title: "Kaushal Sham",
      img: "https://i.pinimg.com/564x/35/ca/ed/35caed9ed16376c0a35e93354952759e.jpg",
      projName: "Monoco - Matic",
    },
  ];

  $: blog_details = [];

  onMount(async () => {
    await getData();
  });
  let getData = async () => {
    let { data, error } = await supabase.from("Blog").select("*");
    if (error) {
      console.log(error);
    } else {
      $fufi=data;
      console.log("bhai",$fufi);
      return data;
    }
  };

  // getData();
</script>

<section class="text-gray-600 body-font ">
  <div class="container px-5 py-10 mx-auto">
    <div class="flex flex-wrap w-full mb-10">
      <div class=" w-full mb-6 lg:mb-0">
        <h1
          class="sm:text-4xl text-2xl font-bold title-font mb-2 text-gray-900"
        >
          <span class="text-blue-600">Blog</span> Collection
        </h1>
        <hr />
        <div class="h-[2px] w-full bg-[#0c2079] rounded-md" />
      </div>
    </div>
    <div
      class="flex flex-wrap -m-4 border-2 border-slate-700 rounded-lg px-2 shadow-2xl justify-center shadow-sky-400"
    >
      {#await getData()}
        <p>loading</p>
      {:then items}
        {#each items as item}
        <div class="xl:w-1/4 md:w-1/4 px-3 py-7 w-96">
          <a href="/blog/{item.route}">
            <div class=" p-6 rounded-lg  card_obj">
                <img
                  class="h-40 rounded w-full object-cover object-center mb-5"
                  src={item.image_url}
                  alt="content"
                />
                <h3
                class="tracking-widest text-blue-500 font-semibold text-xs  font-mono title-font"
              >
                {item.first_name + " " + item.last_name}
              </h3>
              <h2
                class="text-lg text-gray-900 font-mono   title-font crd-title"
              >
                {item.blog_title}
              </h2>
            </div>
          </a>
          </div>
        {/each}
      {:catch error}
        <h3 class="text-2xl">Data is Loading</h3>
      {/await}
    </div>
  </div>
</section>

<style>
  .card_obj {
    border: 2px solid black;
    border-radius: 10px;
    transition: all 0.3s ease;
  }
  .card_obj:hover {
    background: #56c1f771;
    transform: translate(-7px, -7px);
    transition: all 0.3s ease;
    box-shadow: 7px 7px 0px #001434;
  }
  .card_obj:hover .crd-title {
    transition: all 0.3s ease;
    color: rgb(5, 87, 209);
  }
</style>
