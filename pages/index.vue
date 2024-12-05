<template>
 <div class=" w-full pl-8  justify-between flex  gap-6 ">
  <div class="  md:w-[790px] mx-auto  h-full  px-[32px] py-[48px]  ">
    <div >
      <h2 class=" text-[#101828]  leading-9 text-3xl  font-semibold">Welcome , <span class="gradient-text text-3xl font-semibold">Mahmoud Ramadn</span></h2>
      <p class=" textpragrhp  font-normal   leading-6  text-[16px] ">Access & manage your account and transactions efficiently.</p>
    </div>

    <div class=" my-6 md:w-full md:h-[168px]  lg:h-[300px] flex  items-center    md:justify-between md:gap-x-10  border-[1px] rounded-md p-6 shadow-md">

  <DonutChart/>
      <div class=" md:w-[511px] lg:w-full h-[120px]   ">

        <div class=" flex  justify-between  mb-4   items-center ">
         <h4>2 Bank Accounts</h4>
         <button class="gradient-text ">+ Add bank</button>
        </div>
 <div class="   w-full  h-16  flex flex-col  justify-between">
  <h4 class=" text-[#475467]  font-medium    text-sm ">Total Current Balance</h4>


  <h3 class=" text-[#101828]  font-bold    text-3xl ">$2,698.12</h3>
 </div>


      </div>

    </div>

     <div>
      <div class="justfiybett my-8 ">
        <h3 class=" text-[#101828] text-4xl   font-semibold">Recent transactions</h3>
        <el-button  class=" w-20  h-10 bg-white text-[#344054]">View All</el-button>

      </div>

       <div >
        <el-tabs v-model="activeName" class="demo-tabs" @tab-click="handleClick">
    <el-tab-pane label="Chase Bank" name="first">
       <div class="  w-full h-[91px] flex items-center  p-4 bg-[#F5FAFF] rounded-lg">
        <div class=" w-full flex   items-start gap-4  ">
          <div class="  w-10 h-10 rounded-full  text-white flex justify-center items-center  bg-[#1570EF]">
            CB
          </div>
            <div class=" w-full flex  justify-between  items-center ">
              <h4 class=" text-[#194185]   text-xl font-bold ">Chase Bank</h4>
              <el-button  style="color:#027A48 ; border: none; background-color:#ECFDF3; border-radius: 70px ;" >savings</el-button>
            </div>

        </div>

       </div>


      <div>
        <el-table :data="tableData" height="250" style="width: 100%">
    <el-table-column
            prop="Transaction"
            label="Transaction"
          >
            <template #default="{ row }">
              <span> <Icon name="logos:spotify-icon" width="36px" height="36px" /> {{   row.Transaction }}</span>
            </template>
          </el-table-column>
    <el-table-column prop="Amount" label="Amount" width="180" />
    <el-table-column prop="Status" label=" Status" />
    <el-table-column prop="Date" label=" Date" />
    <el-table-column prop="Category"  label="Category" />
  </el-table>



      </div>






    </el-tab-pane>
    <el-tab-pane label="Bank of America" name="second"></el-tab-pane>
    <el-tab-pane label="First Platypus Bank" name="third"></el-tab-pane>
  </el-tabs>
       </div>


     </div>





  </div>


  <div class=" md:w-[400px] min-h-scree  border-l-[1px] shadow-sm ">
 <div class=" h-[268px]  relative  ">
  <img class="rounded-tr-3xl" src="../public/img/topsidbar.svg" alt="">

  <div  class="      space-y-3 left-[20px] top-[84px] absolute w-[343px] mb-2 h-[180px]" >
    <div class=" w-[96px] h-[96px]  rounded-full bg-white p-2  shadow-md ">
  <img  class=" w-full h-full" src="../public/img/Avatar.svg" alt="">
 </div>
 <h2 class=" text-[#101828]  font-bold  leading-6 text-xl" >Adrian Hajdin</h2>
  <p class=" text-[#475467]  text-xl leading-5 ">adrian@jsmastery.pro</p>
  </div>




 </div>


 <div class=" h-[274px]  border-b-[1px]    ">
   <div  class=" px-6 flex justify-between items-start">
    <h4 class=" text-[#101828]  text-xl  font-medium ">My Banks</h4>
    <button class="text-[#475467]">+ Add bank</button>
   </div>
   <div class="  w-full   h-[222px]  flex     mt-8   items-end justify-end   relative ">
    <img  class=" " src="../public/img/Horizon Banking App/under.svg" alt="">
    <img  class="   z-10   absolute    bottom-7  right-7   " src="../public/img/Horizon Banking App/above.svg" alt="">

   </div>


 </div>


 <div class="  h-[317px] p-4">
<div class=" flex  justify-between items-start">
  <h2 class=" text-[#101828]  font-semibold text-lg">My budgets</h2>
  <Icon name="mi:options-vertical" width="36px" height="36px" class=" text-[#98A2B3]" />
</div>

<div class=" flex flex-col  gap-2  mt-7 "  v-for="(item,index) in myBudgets" :key="index" >
  <div  class="h-[72px] flex  p-3  rounded-[12px]  justify-center  items-center gap-2  " :class="`bg-[${item.color}]`"  >
    <div class=" w-10 h-10 rounded-full flex items-center  justify-center" :class="`bg-[${item.iconbg}]`">
      <Icon :name='item.icon' width="36px" height="36px" />
    </div>
    <div class="    w-[254px] h-[36px]">
    <div  class=" flex justify-between   items-start " >
      <h5 :class="`text-[${item.descolr}]`">Subscriptions</h5>
      <span :class="`text-[${item.descolr}]`" >$25 left</span>
    </div>

    <div class=" h-[8px] mt-3   rounded-xl  bg-[#D1E9FF]  relative   ">

      <div :class="`w-[${item.pracent}%]` " class=" h-[8px] mt-3   rounded-xl w-[50%] transition-all delay-100  bg-blue-400  ">

      </div>

    </div>


    </div>


  </div>


</div>




</div>

  </div>

 </div>




</template>

<script setup lang="ts">

import DonutChart from '../components/ DonutChart.vue';
import type { TabsPaneContext } from 'element-plus'

definePageMeta({
  layout:'default'
})


const tableData = [
  {
    Transaction: '2016-05-03',
    Amount: 'Tom',
    Status: 'No. 189, Grove St, Los Angeles',
    Date:'23/24/2',
    Category:'subction'

  },

]

const handleClick = () => {
  console.log('click')
}
const activeName = ref('first');


const myBudgets=[
  {
  typs:'Subscriptions',
  budget:'$25 left',
  pracent:70,
  icon:'mdi:monitor',
  color:'#F5FAFF',
  iconbg:'#D1E9FF',
  descolr:'#194185'
},
{
  typs:'Food and booze',
  budget:'$120 left',
  pracent:50,
  icon:"iconamoon:shopping-bag-thin",
  color:'#FEF6FB',
  iconbg:'#C11574',
  descolr:'#851651'
},



]


</script>

<style scoped>


.el-tabs__item.is-active, .el-tabs__item:hover {
  background-image: radial-gradient(circle, #0179FE, #4893FF);
    -webkit-background-clip: text;  /* For Chrome, Safari */
    background-clip: text; /* For other browsers */
    color: transparent;
}
.el-tabs__item {

  color: #667085;
}
.el-table thead  {
    background-color: green;
}
</style>
