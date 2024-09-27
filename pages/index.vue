<template>
  <div class="flex flex-col gap-5 m-5">
    <Table :columns="columns" :data="dataTable" />
    <TreeSelect :data="data" />
  </div>
</template>

<script setup>
const columns = [
  { title: "Name", dataIndex: "name", key: "name" },
  { title: "Age", dataIndex: "age", key: "age" },
  { title: "Address", dataIndex: "address", key: "address" },
  { title: "Tags", dataIndex: "tags", key: "tags" },
];

const dataTable = [
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

const data = ref([
  {
    id: 1,
    name: "Users",
    level: 0,
    children: [
      {
        id: 11,
        name: "Teachers",
        level: 1,
        children: [
          {
            id: 1,
            name: "Students",
            level: 0,
            children: [
              {
                id: 11,
                name: "boys",
                level: 1,
                children: [
                  {
                    id: 111,
                    name: "mukha",
                    level: 2,
                  },
                ],
              },
              {
                id: 12,
                name: "girls",
                level: 1,
              },
            ],
          },
        ],
      },
      {
        id: 12,
        name: "Admins",
        level: 1,
      },
    ],
  },
]);
</script>
