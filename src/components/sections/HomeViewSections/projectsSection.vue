<template>
  <div class=" relative z-0 xl:w-[1280px] xl:m-auto px-2 md:px-4 xl:px-10 ">
    <div class="flex mt-[40px] md:mt-[80px] items-center gap-3 md:gap-6">
      <div>
        <img src="@/assets/icons/logo_left_head.svg" alt="" class="md:w-20 lg:w-15">
      </div>

      <h2 class="text-[46px]  md:text-[80px] lg:text-[65px] font-semibold">
      Наши проекты
      </h2>
    </div>

    <div class=" mt-[22px] md:mt-[28px] md:hidden ">
      <img src="@/assets/img/project1.jpg" alt="" class="w-full rounded-[20px]">
      <img src="@/assets/img/project2.jpg" alt="" class="w-full rounded-[20px] mt-[8px]">
      <img src="@/assets/img/project3.jpg" alt="" class="w-full rounded-[20px] mt-[8px]">

      <img src="@/assets/img/project4.jpg" alt="" class="w-full rounded-[20px] mt-[8px]">

      <div class="flex justify-between gap-[8px] mt-[8px]">
        <div>
          <img src="@/assets/img/project5.jpg" alt="" class="w-full rounded-[20px]">
        </div>

        <div>
          <img src="@/assets/img/project6.jpg" alt="" class="w-full rounded-[20px]">
        </div>
      </div>
    </div>

    <div class="max-md:hidden md:max-lg:flex lg:hidden mt-[28px] flex-col gap-4">
      <div class="flex justify-between gap-4">
        <div class='w-[51%] flex flex-col gap-4'>
          <img src="@/assets/img/project1.jpg" alt="" class="w-full rounded-[25px]">
          <img src="@/assets/img/project3.jpg" alt="" class="w-full rounded-[25px]">
        </div>

        <div class='md:w-[49%]'>
          <img src="@/assets/img/project5.jpg" alt="" class="w-full h-full rounded-[25px]">
        </div>
      </div>

      <div class="flex justify-between gap-4">
        <div class='md:w-[49%]'>
          <img src="@/assets/img/project6.jpg" alt="" class="w-full h-full rounded-[25px]">
        </div>

        <div class='w-[51%] flex flex-col gap-4'>
          <img src="@/assets/img/project2.jpg" alt="" class="w-full rounded-[25px]">
          <img src="@/assets/img/project4.jpg" alt="" class="w-full rounded-[25px] ">
        </div>
      </div>
    </div>

    <div class="max-lg:hidden lg:flex mt-[28px] flex-col gap-3">
      <div class="flex gap-3">
        <div>
          <img src="@/assets/img/project1.jpg" alt="" class=" rounded-[20px]">
        </div>

        <div>
          <img src="@/assets/img/project2.jpg" alt="" class=" rounded-[20px]">
        </div>

        <div>
          <img src="@/assets/img/project3.jpg" alt="" class=" rounded-[20px] ">
        </div>
      </div>

      <div class="flex gap-3">
        <div>
          <img src="@/assets/img/project5.jpg" alt="" class="h-full rounded-[20px]">
        </div>

        <div>
          <img src="@/assets/img/project4.jpg" alt="" class=" rounded-[20px] ">
        </div>

        <div>
          <img src="@/assets/img/project6.jpg" alt="" class="h-full rounded-[20px]">
        </div>
      </div>      
    </div>
  </div>
</template>

<script setup>

</script>
