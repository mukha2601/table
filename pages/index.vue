<template>
  <div>
    <Table :columns="columns" :data="data" />
  </div>
</template>

<script setup>
const columns = [
  { title: "Name", dataIndex: "name", key: "name" },
  { title: "Age", dataIndex: "age", key: "age" },
  { title: "Address", dataIndex: "address", key: "address" },
  { title: "Tags", dataIndex: "tags", key: "tags" },
];

const data = [
  {
    key: 1,
    name: "John Brown",
    age: 32,
    address: "New York No. 1 Lake Park",
    tags: [
      {
        title: "nice",
        color: "bg-green-100 border-green-300",
      },
      {
        title: "developer",
        color: "bg-blue-100 border-blue-300",
      },
    ],
  },
  {
    key: 2,
    name: "Jim Green",
    age: 42,
    address: "London No. 1 Lake Park",
    tags: [
      {
        title: "looser",
        color: "bg-red-100 border-red-300",
      },
    ],
  },
  {
    key: 3,
    name: "Joe Black",
    age: 32,
    address: "Sidney No. 1 Lake Park",
    tags: [
      {
        title: "cool",
        color: "bg-green-100 border-green-300",
      },
      {
        title: "teacher",
        color: "bg-blue-100 border-blue-300",
      },
    ],
  },
];
</script>
