<script>
  /**
   * @type {{ title: any; subtitle: any; des: any; }}
   */
  export let tifu;
  let isVisible = 1;
</script>

<section class="bg-white dark:bg-gray-900">
  <div
    class="grid max-w-screen-xl px-4 py-8 mx-auto lg:gap-8 xl:gap-0 lg:py-16 lg:grid-cols-12"
  >
    <div class="mr-auto place-self-center lg:col-span-7">
      <h1
        class="max-w-2xl mb-4 text-4xl font-extrabold tracking-tight leading-none md:text-5xl xl:text-6xl  heroTitle text-[#80ed99]"
      >
        {tifu.title} <span class="text-white"> Within Few Seconds</span>
      </h1>
      <p
        class="max-w-2xl mb-6 font-light text-gray-500 lg:mb-8 md:text-lg lg:text-xl dark:text-gray-400"
      >
        {tifu.des}
      </p>
      <!-- svelte-ignore a11y-mouse-events-have-key-events -->
      <a
        href="/upload"
        class="inline-flex align-middle   items-center justify-center px-5 py-3 mr-3 text-base font-medium text-center text-white rounded-lg bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:ring-primary-300 dark:focus:ring-primary-900 hover:text-[#80ed99] "
        on:mouseenter={() => {
          isVisible = 2;
        }}
        on:mouseleave={() => {
          isVisible = 1;
        }}
      >
        Upload
        <svg
          class="w-5 h-5 ml-2 -mr-1  transition-all duration-200 {isVisible ===
          2
            ? 'translate-x-3'
            : ''} "
          fill="currentColor"
          viewBox="0 0 20 20"
          xmlns="http://www.w3.org/2000/svg"
          ><path
            fill-rule="evenodd"
            d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
            clip-rule="evenodd"
          /></svg
        >
      </a>
      <a
        href="/blog"
        class="inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-gray-900 border-2 border-[#80ed99]  rounded-lg hover:bg-sky-400   dark:text-white  dark:hover:bg-[#80ed99] dark:focus:ring-gray-800 hover:text-gray-900"
      >
        Blogs
      </a>
    </div>
    <div class="hidden lg:mt-0 lg:col-span-5 lg:flex ">
      <img
        src="https://img.freepik.com/free-vector/social-biography-concept-illustration_114360-5117.jpg?w=740&t=st=1679224183~exp=1679224783~hmac=988262c37f42cf642d6c50d22e12c8ec6d33a9f6d583c1c460a7502eab399896"
        alt="mockup"
        class="heroimg hover:border-gray-900 border-2"
      />
    </div>
  </div>
</section>

<style>
  .heroimg {
    border-radius: 10px;
    transition: all 0.3s ease;
  }
  .heroimg:hover {
    transition: all 0.3s ease;
    transform: translate(-20px, -10px);
    box-shadow: 10px 10px #80ed99;
  }
</style>
