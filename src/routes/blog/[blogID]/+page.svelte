<script>
// @ts-nocheck
  import {onMount} from "svelte";
  import supabase from "$lib/db";
  import { page } from "$app/stores";
  $: RouteID = $page.params.blogID;
  $: fufiData =[];

  onMount(async () => {
    await getData();
  });
  let getData = async () => {
    let { data, error } = await supabase.from("Blog").select("*").eq("route",RouteID);
    
    console.log(data);
    if (error) {
      console.log(error);
    } else {
      fufiData=data;
      return data;
    }
  };

  $: console.log(fufiData,"fufiData");
</script>
{#await getData() then data}

<div class="bg-white py-6 sm:py-8 lg:py-12">
  <div class="mx-auto max-w-screen-md px-4 md:px-8">

    <!-- svelte-ignore a11y-missing-attribute -->
    <a
    class="relative block overflow-hidden rounded-xl   md:h-96 h-64 popy"
    style="background-image: url({data[0].image_url});"
>
  <div class="absolute inset-0 bg-black/25"></div>

  <div class="relative flex items-start justify-between p-4 sm:p-6 lg:p-8">
    <div class="sm:pt-18 pt-44 text-white lg:pt-72">
      <h3 class="text-xl font-bold sm:text-2xl ">{data[0].first_name + " " +data[0].last_name}</h3>

      <p class="text-sm">{data[0].created_at}</p>
    </div>

    <div class="flex ">
      <a href={data[0].insta_url} target="_blank" class="text-white mx-1 transition duration-100 hover:text-gray-900 active:text-gray-600">
        <svg class="h-5 w-5" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z" />
        </svg>
      </a>
  
      <a href={data[0].linkedin_url} target="_blank" class="text-white mx-1 transition duration-100 hover:text-gray-900 active:text-gray-600">
        <svg class="h-5 w-5" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
          <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" />
        </svg>
      </a>
    </div>
  </div>
</a>


    <!-- <div class="relative mb-6 overflow-hidden rounded-lg bg-gray-100 shadow-lg md:mb-8">
      <img src="https://images.unsplash.com/photo-1593508512255-86ab42a8e620?auto=format&q=75&fit=crop&w=600&h=350" loading="lazy" alt="Photo by Minh Pham" class="h-full w-full object-cover object-center" />
    </div> -->

    <h1 class="mb-4 text-center text-2xl font-bold text-gray-800 mt-3  sm:text-4xl md:mb-6">{data[0].blog_title}</h1>

    <p class="mb-6 text-gray-500 sm:text-lg md:mb-8">
      {data[0].blog_content}
    </p>

  </div>
</div>
{/await}

<style>
  .popy {
    height: 400px;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  @media (max-width: 640px) {
    .popy {
      height: 270px;
    }
  }
</style>