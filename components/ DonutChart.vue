<template>
  <div>
    <!-- هنا يتم عرض الرسم البياني -->
    <Doughnut :data="chartData" :options="chartOptions" class=" md:w-32 md:h-32 lg:w-52 lg:h-52"  />
  </div>
</template>

<script setup>
// استيراد مكونات Chart.js من vue-chartjs
import { Doughnut } from 'vue-chartjs';
import { reactive } from 'vue'; // للتفاعل مع البيانات
import { ArcElement, Chart as ChartJS, Title, Tooltip, Legend } from 'chart.js';

// تسجيل العناصر اللازمة من Chart.js
ChartJS.register(ArcElement, Title, Tooltip, Legend);

// إعداد بيانات الرسم البياني
const chartData = reactive({
  // labels: ['أحمر', 'أزرق', 'أصفر'],
  datasets: [
    {
      label: 'الرسم البياني الدونات',
      data: [200, 150, 100,50,60],
      backgroundColor: ['#4893FF', '#0179FE', '#BED9FF','#85B7FF','#E9F2FF'],
      borderWidth: 1
    }
  ]
});

// إعداد خيارات الرسم البياني (مثل الألوان والموقع)
const chartOptions = reactive({
  responsive: true,
  plugins: {
    legend: {
      position: 'top'
    }
  },
    cutout: '70%'
});
</script>


<style scoped>
/* هنا يمكن إضافة أي أنماط إضافية */
</style>
