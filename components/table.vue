<template>
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
        <tr v-for="(row, index) in users" :key="row.key">
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
                  :class="[
                    'tag border-2 px-2 rounded-md',
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
          <td
            class="border border-gray-200 px-4 py-2 text-red-600 cursor-pointer"
          >
            <button class="border-2 bg-red-100 border-red-300 px-4 rounded-md" @click="deleteItem(index)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
</template>

<script setup>
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

const users = ref([...props.data]);
const deleteItem = (index) => {
  users.value.splice(index, 1); 
};
</script>
