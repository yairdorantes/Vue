<script setup>
import { computed, ref } from "vue";
let isActive = ref(true);
const counter = ref(0);
const items = ref([]);
const name = "Yair";
const myList = [1, 2, 3, 4, 5, 6, 7];
console.log(`hello world! ${4 + 7}`);
const emojis = [
  "✌",
  "😂",
  "😝",
  "😁",
  "😱",
  "👉",
  "🙌",
  "🍻",
  "🔥",
  "🌈",
  "☀",
  "🎈",
];
const people = [
  {
    name: "John Doe",
    age: 30,
    gender: "Male",
    occupation: "Engineer",
  },
  {
    name: "Jane Smith",
    age: 25,
    gender: "Female",
    occupation: "Teacher",
  },
  {
    name: "Bob Johnson",
    age: 40,
    gender: "Male",
    occupation: "Doctor",
  },
  // Add more person objects as needed
];

const print = (name) => {
  alert(`hello world! ${name}`);
};
const handleActivce = () => {
  isActive.value = !isActive.value;
};
const increment = () => {
  counter.value++;
};
const dicrement = () => {
  counter.value--;
};

const addItem = () => {
  items.value.push(counter.value);
};

const delItem = () => {
  items.value = items.value.slice(0, -1);
};
const classComputer = computed(() => {
  if (counter.value === 0) {
    return "text-info";
  } else if (counter.value > 0) {
    return "text-success";
  } else if (counter.value < 0) {
    return "text-error";
  }
});
// const styleColor = "background-color:blue";
let styleColor = {
  backgroundColor: isActive ? "black" : "transparent",
};
</script>
<template>
  <h1 class="text-green-500" :style="styleColor">
    hello world from vue with {{ name.toUpperCase() }} {{ myList }}
  </h1>
  <div class="badge badge-secondary">
    isActive? -

    {{ isActive ? "Is active" : "not active" }}
  </div>
  <p v-if="!isActive">test directives</p>
  <p v-else>Im active</p>
  <div v-show="isActive">active with show</div>
  <ul class="flex gap-2">
    <li
      class="btn btn-circle btn-primary"
      v-for="(emoji, i) in emojis"
      :key="i"
    >
      {{ emoji }}-{{ i + 1 }}
    </li>
  </ul>
  <!-- v-show make display none -->
  <button @click="handleActivce" class="btn btn-secondary">
    Toggle active
  </button>
  <button @click.middle="print('yair')" class="btn btn-success mt-10">
    click
  </button>
  <div class="text-xl font-bold" :class="classComputer">
    {{ counter }}
  </div>

  <h2 class="mb-2 text-lg font-semibold text-gray-900 dark:text-white">
    Items:
  </h2>
  <ul
    class="max-w-md space-y-1 text-gray-500 list-disc list-inside dark:text-gray-400"
  >
    <li v-for="(item, i) in items" :key="i">
      {{ item }}
    </li>
  </ul>

  <button @click="increment" class="btn btn-success">increment</button>
  <button @click="dicrement" class="btn btn-error">dicrement</button>
  <button
    @click="addItem"
    :disabled="items.includes(counter)"
    class="btn btn-success"
  >
    ADD
  </button>
  <button @click="delItem" class="btn btn-error uppercase">Delete</button>
  <div class="flex gap-2 justify-center">
    <template v-for="(person, i) in people" class="" :key="i">
      <div v-if="person.gender === 'Male'">
        <div
          class="relative flex flex-col mt-6 text-gray-700 bg-white shadow-md bg-clip-border rounded-xl"
        >
          <div
            class="relative h-56 mx-4 -mt-6 overflow-hidden text-white shadow-lg bg-clip-border rounded-xl bg-blue-gray-500 shadow-blue-gray-500/40"
          >
            <img
              src="https://images.unsplash.com/photo-1540553016722-983e48a2cd10?ixlib=rb-1.2.1&amp;ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&amp;auto=format&amp;fit=crop&amp;w=800&amp;q=80"
              alt="card-image"
            />
          </div>
          <div class="p-6">
            <h5
              class="block mb-2 font-sans text-xl antialiased font-semibold leading-snug tracking-normal text-blue-gray-900"
            >
              {{ person.name }}
            </h5>
            <p
              class="block font-sans text-base antialiased font-light leading-relaxed text-inherit"
            >
              {{ person.age }}
              {{ person.gender }}
            </p>
          </div>
          <div class="p-6 pt-0">
            <button
              class="align-middle select-none font-sans font-bold text-center uppercase transition-all disabled:opacity-50 disabled:shadow-none disabled:pointer-events-none text-xs py-3 px-6 rounded-lg bg-gray-900 text-white shadow-md shadow-gray-900/10 hover:shadow-lg hover:shadow-gray-900/20 focus:opacity-[0.85] focus:shadow-none active:opacity-[0.85] active:shadow-none"
              type="button"
            >
              {{ person.occupation }}
            </button>
          </div>
        </div>
      </div>
    </template>
  </div>
</template>
<!-- directivess -->
