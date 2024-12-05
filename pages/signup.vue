
<template>
  <div class="  col-span-3 flex items-center justify-center  ">
    <div class=" w-[460px] h-[824px]    ">
      <div class=" flex items-center gap-2">
        <img src="/img/logo.svg" alt="">
        <h1 class=" primary  font-bold  text-3xl ">Horizon</h1>
      </div>

     <div class="  my-3 space-y-3 ">
      <h1 class="primary  secondy font-bold    leading-10  text-4xl">Sign up</h1>
      <p class=" textpragrhp   text-[16px] leading-6 ">Please enter your details.</p>
     </div>


     <form >

      <div class="  my-3 flex items-start  justify-between">
        <div class="dircol " >
        <label for="firstName" class="   text-sm  label font-bold ">First Name</label>
        <input class=" h-11  w-[221px] pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="firstName"  type="text" placeholder="John"  />
      </div>
      <div class="dircol " >
        <label for="lastName" class="   text-sm  label font-bold ">Last Name</label>
        <input class=" h-11   w-[221px] pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="lastName"  type="text" placeholder="ex: Doe"  />
      </div>


      </div>

      <div class="dircol my-3 " >
        <label for="address" class="text-sm  label font-bold ">Address</label>
        <input class=" h-11  pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="address"  type="text" placeholder="Enter your specific address" />
      </div>


      <div class=" flex items-start  my-3 justify-between">
        <div class="dircol " >
        <label for="state" class="text-sm  label font-bold ">State</label>
        <input class=" h-11  w-[221px] pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="state"  type="text" placeholder="ex: NY"  />
      </div>
      <div class="dircol " >
        <label for="postalcode" class="   text-sm  label font-bold ">Postal Code</label>
        <input class=" h-11  w-[221px] pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="postalcode"  type="lastName" placeholder="ex: 11101"  />
      </div>


      </div>

      <div class=" flex items-start my-3 justify-between">
        <div class="dircol " >
        <label for="dateBirth" class="   text-sm  label font-bold ">Date of Birth</label>
        <input class=" h-11  w-[221px] pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="dateBirth"  type="date" placeholder="yyyy-mm-dd"  />
      </div>
      <div class="dircol " >
        <label for="SSN" class="   text-sm  label font-bold ">SSN</label>
        <input class=" h-11  w-[221px]  pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="SSN"   type="number" placeholder="ex: 1234"  />
      </div>


      </div>




      <div class="dircol my-3  " >
        <label for="Email" class="   text-sm  label font-bold ">Email</label>
        <input class=" h-11  pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="Email"  type="email" placeholder="Enter your email" />
      </div>



      <div class="dircol my-3 " >
        <label for="password" class="   text-sm  label font-bold ">Password</label>
        <input class=" h-11  pl-4 placeholder:placehoder  border-[1px]
       border-[border] rounded-lg
        focus:outline-gray-500
        " id="password"  type="password" placeholder="Enter your password" />
      </div>

      <button   class="authBtn"   type="submit">Sign up</button>
      <p class=" textpragrhp  text-center my-5">Don’t have an account? <NuxtLink  to="/login"class="gradient-text">Login</NuxtLink></p>
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
