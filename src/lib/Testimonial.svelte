<script>
  let data = [
    {
      name: "HOLDEN CAULFIELD",
      des: "Senior Product Designer",
      img: "https://dummyimage.com/302x302",
      text: "Edison bulb retro cloud bread echo park, helvetica stumptown taiyaki taxidermy 90's cronut +1 kinfolk. Single-origin coffee ennui shaman taiyaki vape DIY tote bag drinking vinegar cronut adaptogen squid fanny pack vaporware.",
    },
    {
      name: "ALPER KAMU",
      des: "UI Develeoper",
      img: "https://dummyimage.com/300x300",
      text: "Edison bulb retro cloud bread echo park, helvetica stumptown taiyaki taxidermy 90's cronut +1 kinfolk. Single-origin coffee ennui shaman taiyaki vape DIY tote bag drinking vinegar cronut adaptogen squid fanny pack vaporware.",
    },
    {
      name: "HENRY LETHAM",
      des: "CTO",
      img: "https://dummyimage.com/305x305",
      text: "Edison bulb retro cloud bread echo park, helvetica stumptown taiyaki taxidermy 90's cronut +1 kinfolk. Single-origin coffee ennui shaman taiyaki vape DIY tote bag drinking vinegar cronut adaptogen squid fanny pack vaporware.",
    },
  ];
</script>

<section class="text-blue-900 body-font ">
  <div class="container px-5 py-5 md:py-24 mx-auto ">
    <div
      class="flex flex-wrap -m-4"
      data-aos="fade-up"
      data-aos-offset="200"
      data-aos-delay="50"
      data-aos-duration="1000"
      data-aos-easing="ease-in-out"
      data-aos-mirror="true"
      data-aos-once="false"
    >
      {#each data as item}
        <div class="p-4 md:w-1/3 ">
          <div
            class="h-full bg-green-200 bg-opacity-75 py-4  md:px-10 md:py-10 overflow-hidden text-center relative border-gray-900 border-2 rounded-2xl"
          >
            <img
              alt="testimonial"
              class="w-20 h-20 mb-8 object-cover object-center rounded-full inline-block border-2 border-gray-200 bg-gray-200"
              src={item.img}
            />
            <p class="leading-relaxed">{item.text}</p>
            <span
              class="inline-block h-1 w-10 rounded bg-indigo-500 mt-6 mb-4"
            />
            <h2
              class="text-gray-900 font-medium title-font tracking-wider text-sm"
            >
              {item.name}
            </h2>
            <p class="text-gray-500">{item.des}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
