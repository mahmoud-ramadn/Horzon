<template>
  <div class="  col-span-3 flex items-center justify-center ">
    <div class=" w-[360px] h-[464px]   ">
      <div class=" flex items-center gap-2">
        <img src="/img/logo.svg" alt="">
        <h1 class=" primary  font-bold  text-3xl ">Horizon</h1>
      </div>

     <div class=" my-6 space-y-3 ">
      <h1 class="primary  secondy font-bold    leading-10  text-4xl">Log in</h1>
      <p class=" textpragrhp   text-[16px] leading-6 ">Welcome back! Please enter your details.</p>
     </div>


     <form >
      <div class="dircol " >
        <label for="Email" class="   text-sm  label font-bold ">Email</label>
        <input class=" h-11  pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="Email"  type="email" placeholder="Enter your email" />
      </div>
      <div class="dircol my-6" >
        <label for="password" class="   text-sm  label font-bold ">Password</label>
        <input class=" h-11  pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="password"  type="password" placeholder="Enter your password" />
      </div>

      <button   class="authBtn"   type="submit">Login</button>
      <p class=" textpragrhp  text-center my-5">Don’t have an account? <NuxtLink  to="/signup"class="gradient-text">signUp</NuxtLink></p>
     </form>



    </div>

  </div>
</template>

<script setup lang="ts">


definePageMeta({
  layout:'loginglayout'
})

</script>

<style scoped>

</style>
