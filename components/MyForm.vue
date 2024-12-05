<template>
  <div class="container mx-auto flex flex-col justify-center items-center min-h-screen">
    <el-form @submit.prevent="onSubmit" :model="formData" label-width="auto" style="max-width: 600px; display: flex; flex-direction: column; gap: 10px;">
      <el-input
        v-model="formData.name"
        style="width: 240px"
        placeholder="Enter your name"
      >
        <template #prefix>
          <el-icon class="el-input__icon"><User /></el-icon>
        </template>
      </el-input>

      <el-input
        v-model="formData.email"
        type="email"
        style="width: 240px"
        placeholder="Type your Email"
      >
        <template #prefix>
          <el-icon class="el-input__icon"><Message /></el-icon>
        </template>
      </el-input>

      <el-input
        v-model="formData.password"
        style="width: 240px"
        type="password"
        placeholder="Please input password"
        show-password
      >
        <template #prefix>
          <el-icon class="el-input__icon"><Lock /></el-icon>
        </template>
      </el-input>

      <!-- الزر مع تعطيله إذا كانت الحقول غير مكتملة -->
      <button
        :type="'submit'"
        :disabled="!isFormValid"
        class="w-[300px] p-4 bg-blue-400 rounded-md text-2xl font-bold"
      >
        {{ loading ? 'loading' : 'Submit' }}
      </button>
    </el-form>
  </div>
</template>

<script lang="ts" setup>
import { User, Message, Lock } from '@element-plus/icons-vue';
import { formMetaProps } from 'element-plus';

const formData = reactive({
  name: '',
  email: '',
  password: ''
});

const loading = ref(false);

// التحقق من صحة البيانات (هل جميع الحقول مكتملة)
const isFormValid = computed(() => {
  return formData.name && formData.email && formData.password; // تأكد من أن جميع الحقول غير فارغة
});




// دالة الإرسال
const onSubmit = () => {
  if (!isFormValid.value) return; // منع الإرسال إذا كانت الحقول غير مكتملة
  loading.value = true;
  console.log(formData);
  // محاكاة عملية تحميل ثم إعادة تعيين قيمة "التحميل"
  setTimeout(() => {
    loading.value = false;
    // هنا يمكنك تنفيذ الكود بعد الإرسال مثل مسح البيانات أو توجيه المستخدم
  }, 2000);
};
</script>
