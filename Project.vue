<template>

  <div class="flex flex-col items-center h-screen">
    
    <div class="container mx-auto p-4">
       <h1 class="text-2xl font-bold mb-4">Front-End Task - Vikram  </h1>
      <h1 class="text-2xl font-bold mb-4">To-Do Lists</h1>

      <div class="flex mb-4">
        <input
          v-model="newItemText"
          class="border rounded-l px-4 py-2 flex-1"
          placeholder="Add a new item"
          @keyup.enter="addItem"
        />
        <button class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-r" @click="addItem">Add</button>
      </div>

      <div>
        <h2 class="text-xl font-bold mb-2">Folder: {{ currentFolder }}</h2>
        <ul class="list-disc pl-8">
          <li v-for="(item, index) in items" :key="index" :class="{ 'line-through': item.completed }">
            {{ item.text }}
            <button class="ml-2 text-red-500" @click="deleteItem(index)">Delete</button>
            <button class="ml-2 text-blue-500" @click="toggleComplete(index)">
              {{ item.completed ? 'Mark Incomplete' : 'Mark Complete' }}
            </button>
          </li>
        </ul>
      </div>

      <div class="mt-4">
        <h2 class="text-xl font-bold mb-2">Folders</h2>
        <select class="border rounded px-4 py-2" v-model="currentFolder" @change="changeFolder">
          <option v-for="(folder, index) in folders" :key="index">{{ folder }}</option>
        </select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentFolder: 'Default',
      newItemText: '',
      items: [],
      folders: ['Default', 'Work', 'Personal']
    };
  },
  methods: {
    addItem() {
      if (this.newItemText.trim() !== '') {
        this.items.push({
          text: this.newItemText,
          completed: false
        });
        this.newItemText = '';
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1);
    },
    toggleComplete(index) {
      this.items[index].completed = !this.items[index].completed;
    },
    changeFolder(event) {
      this.currentFolder = event.target.value;
    }
  }
};
</script>
<style scoped>
.container {
  background-color: #f3f4f6;
  padding: 2rem;
}

input[type="text"] {
  border: 1px solid #ddd;
  border-radius: 0.25rem 0 0 0.25rem;
  padding: 0.5rem;
  flex: 1;
}

button {
  border: none;
  border-radius: 0.25rem;
  padding: 0.5rem;
  cursor: pointer;
}

button.bg-blue-500 {
  background-color: #3b82f6;
}

button.bg-blue-500:hover {
  background-color: #2563eb;
}

button.text-red-500 {
  color: #ef4444;
}

button.text-blue-500 {
  color: #3b82f6;
}

.line-through {
  text-decoration: line-through;
}

ul {
  padding-left: 2rem;
}

li {
  margin-bottom: 0.5rem;
}

.cursor-pointer {
  cursor: pointer;
}

.text-xl {
  font-size: 1.25rem;
}

.text-2xl {
  font-size: 1.5rem;
}

.font-bold {
  font-weight: bold;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.mt-4 {
  margin-top: 1rem;
}

.pl-8 {
  padding-left: 2rem;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

/* Additional Tailwind CSS classes for colorful styling */

.container {
  background-color: #f3f4f6;
  padding: 2rem;
}

input[type="text"] {
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  padding: 0.5rem;
}

button {
  border-radius: 0.25rem;
  padding: 0.5rem;
  cursor: pointer;
}

button.bg-blue-500 {
  background-color: #3b82f6;
}

button.bg-blue-500:hover {
  background-color: #2563eb;
}

button.text-red-500 {
  color: #ef4444;
}

button.text-blue-500 {
  color: #3b82f6;
}

.line-through {
  text-decoration: line-through;
}

ul {
  padding-left: 2rem;
}

li {
  margin-bottom: 0.5rem;
}

.cursor-pointer {
  cursor: pointer;
}

.text-xl {
  font-size: 1.25rem;
}

.text-2xl {
  font-size: 1.5rem;
}

.font-bold {
  font-weight: bold;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.mt-4 {
  margin-top: 1rem;
}

.pl-8 {
  padding-left: 2rem;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

/* Additional colorful styles */

.container {
  background-color: #f3f4f6;
  padding: 2rem;
}

input[type="text"] {
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  padding: 0.5rem;
}

button {
  border-radius: 0.25rem;
  padding: 0.5rem;
  cursor: pointer;
}

button.bg-blue-500 {
  background-color: #3b82f6;
}

button.bg-blue-500:hover {
  background-color: #2563eb;
}

button.text-red-500 {
  color: #ef4444;
}

button.text-blue-500 {
  color: #3b82f6;
}

.line-through {
  text-decoration: line-through;
}

ul {
  padding-left: 2rem;
}

li {
  margin-bottom: 0.5rem;
}

.cursor-pointer {
  cursor: pointer;
}

.text-xl {
  font-size: 1.25rem;
}

.text-2xl {
  font-size: 1.5rem;
}

.font-bold {
  font-weight: bold;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.mt-4 {
  margin-top: 1rem;
}

.pl-8 {
  padding-left: 2rem;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

/* Colorful styles */

.container {
  background-color: #f3f4f6;
  padding: 2rem;
}

input[type="text"] {
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  padding: 0.5rem;
}

button {
  border-radius: 0.25rem;
  padding: 0.5rem;
  cursor: pointer;
}

button.bg-blue-500 {
  background-color: #3b82f6;
}

button.bg-blue-500:hover {
  background-color: #2563eb;
}

button.text-red-500 {
  color: #ef4444;
}

button.text-blue-500 {
  color: #3b82f6;
}

.line-through {
  text-decoration: line-through;
}

ul {
  padding-left: 2rem;
}

li {
  margin-bottom: 0.5rem;
}

.cursor-pointer {
  cursor: pointer;
}

.text-xl {
  font-size: 1.25rem;
}

.text-2xl {
  font-size: 1.5rem;
}

.font-bold {
  font-weight: bold;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.mt-4 {
  margin-top: 1rem;
}

.pl-8 {
  padding-left: 2rem;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

/* Additional colorful styles */

.container {
  background-color: #f3f4f6;
  padding: 2rem;
}

input[type="text"] {
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  padding: 0.5rem;
}

button {
  border-radius: 0.25rem;
  padding: 0.5rem;
  cursor: pointer;
}

button.bg-blue-500 {
  background-color: #3b82f6;
}

button.bg-blue-500:hover {
  background-color: #2563eb;
}

button.text-red-500 {
  color: #ef4444;
}

button.text-blue-500 {
  color: #3b82f6;
}

.line-through {
  text-decoration: line-through;
}

ul {
  padding-left: 2rem;
}

li {
  margin-bottom: 0.5rem;
}

.cursor-pointer {
  cursor: pointer;
}

.text-xl {
  font-size: 1.25rem;
}

.text-2xl {
  font-size: 1.5rem;
}

.font-bold {
  font-weight: bold;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.mt-4 {
  margin-top: 1rem;
}

.pl-8 {
  padding-left: 2rem;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

/* Colorful styles */

.container {
  background-color: #f3f4f6;
  padding: 2rem;
}

input[type="text"] {
  border: 1px solid #ddd;
  border-radius: 0.25rem;
  padding: 0.5rem;
}

button {
  border-radius: 0.25rem;
  padding: 0.5rem;
  cursor: pointer;
}

button.bg-blue-500 {
  background-color: #3b82f6;
}

button.bg-blue-500:hover {
  background-color: #2563eb;
}

button.text-red-500 {
  color: #ef4444;
}

button.text-blue-500 {
  color: #3b82f6;
}

.line-through {
  text-decoration: line-through;
}

ul {
  padding-left: 2rem;
}

li {
  margin-bottom: 0.5rem;
}

.cursor-pointer {
  cursor: pointer;
}

.text-xl {
  font-size: 1.25rem;
}

.text-2xl {
  font-size: 1.5rem;
}

.font-bold {
  font-weight: bold;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.mt-4 {
  margin-top: 1rem;
}

.pl-8 {
  padding-left: 2rem;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}
</style>
