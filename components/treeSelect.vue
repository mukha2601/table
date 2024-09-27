<template>
  <div class="w-[400px] overflow-hidden">
    <ul class="bg-gray-100 cursor-pointer">
      <li
        v-for="item in data"
        :key="item.id"
        class="w-full cursor-pointer select-none"
        :class="item.selected ? 'ps-4' : ''"
      >
        <div
          @click="toggle(item)"
          class="flex gap-4 items-center p-2 px-4 border-s-4 border-transparent hover:bg-gray-300 hover:border-blue-600"
        >
          <span v-if="item.children">
            <img src="../assets/down.png" alt="" class="w-2" />
          </span>
          <span class="text-lg">{{ item.name }}</span>
        </div>

        <ul v-if="item.showChildren && item.children">
          <TreeSelect :data="item.children" />
        </ul>
      </li>
    </ul>
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Array,
    required: true,
  },
});

const toggle = (item) => {
  if (item.children) {
    item.showChildren = !item.showChildren;
    item.selected = !item.selected;
  }
};
</script>
