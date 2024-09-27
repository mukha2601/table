<template>
    <div class="m-5">
      <table class="min-w-full border-collapse border border-gray-200">
        <thead>
          <tr class="bg-gray-100">
            <th
              v-for="column in columns"
              :key="column.key"
              class="border border-gray-200 px-4 py-2 text-left"
            >
              {{ column.title }}
            </th>
            <th class="border border-gray-200 px-4 py-2 text-left">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(row, index) in data" :key="row.key">
            <td
              v-for="column in columns"
              :key="column.key"
              class="border border-gray-200 px-4 py-2"
            >
              <template v-if="column.dataIndex === 'tags'">
                <div class="flex gap-4">
                  <span
                    v-for="tag in row[column.dataIndex]"
                    :key="tag.key"
                    :class="['tag border-2 px-2 rounded-md',
                      tag ? tag.color : '',
                    ]"
                  >
                    {{ tag.title?.toUpperCase() }}
                  </span>
                </div>
              </template>
              <template v-else>
                {{ row[column.dataIndex] }}
              </template>
            </td>
            <!-- Delete tugmasi -->
            <td class="border border-gray-200 px-4 py-2 text-red-600 cursor-pointer">
              <button @click="removeRow(index)">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const props = defineProps({
    columns: {
      type: Array,
      required: true,
    },
    data: {
      type: Array,
      required: true,
    },
  });
  
  const localData = ref([...props.data]);
  
  const removeRow = (index) => {
    localData.value.splice(index, 1); // index bo'yicha qatorni o'chiramiz
  };
  </script>
  