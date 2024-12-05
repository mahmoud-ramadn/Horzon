<template>
  <div>
    <el-table :data="paginatedData" height="250" style="width: 100%; overflow-x: auto;">
      <!-- Column for 'Date' -->
      <el-table-column prop="date" label="Date" :min-width="100" style="display: flex; align-items: center;">
        <template #default="{ row }">
          <div >

            <el-checkbox />
            <span >{{ row.date }}</span>
          </div>
        </template>
      </el-table-column>

      <!-- Profile Link Column -->
      <el-table-column prop="name" label="Name" :min-width="100">
        <template #default="{ row }">
          <!-- Dynamically generated profile link for each row based on the 'id' or unique field -->
          <nuxt-link :to="`/profile/${row.id}`">
            {{ row.name }}
          </nuxt-link>
        </template>
      </el-table-column>

      <!-- Other columns -->
      <el-table-column prop="address" label="Address" />
      <el-table-column prop="email" label="Email" />
      <el-table-column prop="jobTitle" label="Job Title" />
    </el-table>

    <!-- Custom Pagination with Basic HTML Buttons -->
    <div class="pagination-container">
      <button
        class="pagination-button"
        :disabled="currentPage === 1"
        @click="handlePageChange(currentPage - 1)"
      >
        Previous
      </button>
      <span class="pagination-info">
        Page {{ currentPage }} of {{ totalPages }}
      </span>
      <button
        class="pagination-button"
        :disabled="currentPage === totalPages"
        @click="handlePageChange(currentPage + 1)"
      >
        Next
      </button>
    </div>
  </div>
</template>


<script lang="ts" setup>
import { ref, computed } from 'vue';

const tableData = [
  { id: 1, date: '2016-05-03', name: 'Tom', address: 'No. 189, Grove St, Los Angeles', email: 'tom@example.com', jobTitle: 'UI/UX Designer' },
  { id: 2, date: '2016-05-02', name: 'Jerry', address: 'No. 190, Grove St, Los Angeles', email: 'jerry@example.com', jobTitle: 'Developer' },
  { id: 3, date: '2016-05-04', name: 'Mickey', address: 'No. 191, Grove St, Los Angeles', email: 'mickey@example.com', jobTitle: 'Product Manager' },
  { id: 4, date: '2016-05-01', name: 'Donald', address: 'No. 192, Grove St, Los Angeles', email: 'donald@example.com', jobTitle: 'Designer' },
  { id: 5, date: '2016-05-08', name: 'Goofy', address: 'No. 193, Grove St, Los Angeles', email: 'goofy@example.com', jobTitle: 'Marketer' },
  { id: 6, date: '2016-05-06', name: 'Pluto', address: 'No. 194, Grove St, Los Angeles', email: 'pluto@example.com', jobTitle: 'Engineer' },
  { id: 7, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 8, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 9, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 10, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 11, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 12, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 13, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 14, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
  { id: 15, date: '2016-05-07', name: 'Chip', address: 'No. 195, Grove St, Los Angeles', email: 'chip@example.com', jobTitle: 'Analyst' },
];

const currentPage = ref(1);
const pageSize = ref(10);

const totalPages = computed(() => {
  return Math.ceil(tableData.length / pageSize.value);
});

const paginatedData = computed(() => {
  const start = (currentPage.value - 1) * pageSize.value;
  const end = start + pageSize.value;
  return tableData.slice(start, end);
});

const handlePageChange = (newPage: number) => {
  if (newPage >= 1 && newPage <= totalPages.value) {
    currentPage.value = newPage;
  }
};
</script>


<style scoped>
.pagination-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.pagination-button {
  padding: 5px 15px;
  background-color: #409EFF;
  border: none;
  color: white;
  font-size: 14px;
  cursor: pointer;
  margin: 0 10px;
}

.pagination-button:disabled {
  background-color: #ccc;
  cursor:not-allowed;
}

.pagination-button:hover:not(:disabled) {
  background-color: #66b1ff;
}

.pagination-info {
  font-size: 14px;
  color: #333;
}
</style>
