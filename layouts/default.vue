<template>
  <div class=" flex  items-start   " >
 <!-- sidbar -->
  <aside class="  w-[280px] min-h-screen  shadow-md bg-white  flex  flex-col justify-between   border-r-[1px]">
 <div class=" w-[280px] h-[452px]  space-y-3    p-7 ">
  <div class=" flex items-center gap-2">
        <img src="/img/logo.svg" alt="">
        <h1 class=" primary  font-bold  text-3xl ">Horizon</h1>
      </div>
      <el-input
      placeholder="Search"
    >
      <template #prefix>
        <el-icon class="el-input__icon"><ElIconSearch/></el-icon>
      </template>
    </el-input>
 <NuxtLink class=" h-[56px] w-full cursor-pointer  flex  items-center gap-x-2 p-3    rounded-md hover:text-white  hover:bg-gradient-to-t from-[#0179FE] to-[#4893FF] "  v-for="(link,index) in sidbarlinks" :key="index">
 <Icon class="   ":name="link.icons"/>
  <h3 class="   t">{{ link.linkeName }}</h3>
 </NuxtLink>



 </div>


 <div  class="   w-full h-[92px] border-t-[1px] flex items-center justify-center ">

  <div class=" flex items-start gap-2">
 <img class=" w-[40px] h-[40px] rounded-none " src="../public/img/Avatar.svg" alt="">
 <div>

  <h5 class=" font-semibold   text-sm  text-[#344054] ">Adrian Hajdin</h5>
   <small class="   font-normal   text-sm  text-[#475467]">adrian@jsmastery.pro</small>
 </div>
 <span class=" w-10 h-10 self-center  flex items-center justify-center">
  <Icon class=" cursor-pointer    " name="material-symbols-light:logout" width="36px" height="36px" />
 </span>
  </div>



 </div>

  </aside>
<div  class="  w-full ">

    <slot/>
</div>
  </div>
</template>

<script setup lang="ts">

const sidbarlinks=[
  {
    linkeName:'Home',
    icons:'hugeicons:home-04'
  },
  {
    linkeName:'My Banks',
    icons:"solar:dollar-line-duotone"
  },
  {
    linkeName:'Transaction History',
    icons:'streamline:receipt-check'
  },
  {
    linkeName:'Payment Transfer',
    icons:'hugeicons:money-send-circle'
  },
  {
    linkeName:'Connect Bank',
    icons:"hugeicons:credit-card-add"
  },
]

</script>

<style scoped>

</style>
