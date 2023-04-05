<template>
  <div div class="container mx-auto">
    <p class="h3">CRUD OPERATIONS</p>
  </div>
  <div v-if="isadd">
    <Collection-AddTask />
  </div>
  <div v-if="isEdit"><Collection-EditTask /></div>
  <div v-if="isDelete">
    <span v-if="editValue">{{ editValue }}</span>
    <Collection-DeleteTask />
  </div>
  <button type="button" @click="Addtask" class="rounded-md bg-black bg-opacity-20 px-4 py-2 text-sm font-medium text-white hover:bg-opacity-30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75">Add Task</button>
  <div class="px-4 py-6 sm:px-6">
    <ul role="list">
      <div class="card-body space-y-8">
        <div class="card col" v-for="peoples in people" :key="peoples">
          <div>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 sm:py-1 h-6" @click="deleteTask">
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0"
              />
            </svg>
            <div>
              ID - {{ peoples.id }}
              <button @click="editTask()" class="text-sm rounded-md bg-black bg-opacity-20 text-sm hover:bg-opacity-30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75 bg-blue-600">Edit</button>
            </div>
            <div>NAME - {{ peoples.name }}</div>
            <div>TASK - {{ peoples.task }}</div>
            <p>DUE DATE - {{ peoples.due_date }}</p>
          </div>
        </div>
      </div>
    </ul>
  </div>
</template>
<script setup>
  const isadd = ref(false);
  const isEdit = ref(false);
  const isDelete = ref(false);
  let editValue = ref("");
  const people = [
    { id: 789, name: "Durward Reynolds", task: "Work on grid", due_date: "20/4/23" },
    { id: 645, name: "Kenton Towne", task: "Work on delete", due_date: "23/4/23" },
    { id: 565, name: "Therese Wunsch", task: "Work on add", due_date: "25/4/23" },
    { id: 898, name: "Benedict Kessler", task: "Work on edit", due_date: "26/4/23" },
    { id: 128, name: "Katelyn Rohan", task: "Work on tags", due_date: "26/4/23" },
  ];
  function editTask() {
    isEdit.value = true;
  }
  function Addtask() {
    isadd.value = true;
  }
  function deleteTask() {
    isDelete.value = true;
  }
</script>
<style>
  .edit-icon {
    cursor: pointer;
  }
</style>
