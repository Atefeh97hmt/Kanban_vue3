<script setup>
import { ref } from "vue";
const header = ref("Kanban Board");

const toDoItems = ref([
  { id: 1, lable: "buy coffee" },
  { id: 2, lable: "Make cake" },
  { id: 3, lable: "Buy chocolate" },
]);

const doingItems = ref([{ id: 1, lable: "Learning vue" }]);

const doneItems = ref([
  { id: 1, lable: "Doing my homework" },
  { id: 2, lable: "Cook lunch" },
]);

// const items = ref({
// 'item-1': {id: 1, lable: "coffee"},
// 'item-2': {id: 2, lable: "cake"},
// 'item-3': {id: 3, lable: "chocolate"}
// })

const newItemToDo = ref();
const newItemDoing = ref();
const newItemDone = ref();
</script>

<template>
  <h1>{{ header }}</h1>

  <div class="container">
    <div class="row">
      <div class="column">
        <p class="kanbantitle">ToDo</p>
        <ul>
          <!-- <li v-for="item in items" :key="id">{{item.lable}}</li> -->
          <!-- <li v-for="({id, lable}, index) in items" :key="id">{{ index }} {{lable}}</li>  -->

          <div class="additems-container">
            <input
              type="text"
              placeholder="Add an item"
              v-model="newItemToDo"
              @keyup.enter="
                toDoItems.push({ id: toDoItems.length + 1, lable: newItemToDo })
              "
            />
            <button
              @click="
                toDoItems.push({ id: toDoItems.length + 1, lable: newItemToDo })
              "
            >
              save
            </button>
          </div>

          <li v-for="{ id, lable } in toDoItems" :key="id">{{ lable }}</li>
        </ul>
      </div>

      <div class="column">
        <p class="kanbantitle">Doing</p>
        <ul>
          <!-- <li v-for="item in items" :key="id">{{item.lable}}</li> -->
          <!-- <li v-for="({id, lable}, index) in items" :key="id">{{ index }} {{lable}}</li>  -->

          <div class="additems-container">
            <input
              type="text"
              placeholder="Add an item"
              v-model="newItemDone"
              @keyup.enter="
                doingItems.push({
                  id: doingItems.length + 1,
                  lable: newItemDone,
                })
              "
            />
            <button
              @click="
                doingItems.push({
                  id: doingItems.length + 1,
                  lable: newItemDone,
                })
              "
            >
              save
            </button>
          </div>

          <li v-for="{ id, lable } in doingItems" :key="id">{{ lable }}</li>
        </ul>
      </div>

      <div class="column">
        <p class="kanbantitle">Done</p>
        <ul>
          <!-- <li v-for="item in items" :key="id">{{item.lable}}</li> -->
          <!-- <li v-for="({id, lable}, index) in items" :key="id">{{ index }} {{lable}}</li>  -->

          <div class="additems-container">
            <input
              type="text"
              placeholder="Add an item"
              v-model="newItemDoing"
              @keyup.enter="
                items.push({ id: doneItems.length + 1, lable: newItemDoing })
              "
            />
            <button
              @click="
                doneItems.push({
                  id: doneItems.length + 1,
                  lable: newItemDoing,
                })
              "
            >
              save
            </button>
          </div>

          <li v-for="{ id, lable } in doneItems" :key="id">{{ lable }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  display: block;
  color: goldenrod;
  text-align: center;
  width: 100%;
  font-weight: bold;
}

ul {
  list-style: none;
}

li {
  list-style: circle;
  text-align: left;
}
.container {
  margin: 0 auto;
  background-color: #eaeaea;
  max-width: 980px;
  min-width: 320px;
}

.row {
  display: flex;
  flex-wrap: wrap;
}

.column {
  text-align: center;
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 1;
  margin: 10px;
  background-color: #efefef;
  border: 1px solid #dedede;
  padding: 10px;
}

@media screen and (max-width: 768px) {
  .container {
    overflow: auto;
  }
  .column {
    min-width: 100%;
    width: 100%;
    margin: 10px 0;
  }
}
.kanbantitle {
  font-size: 20px;
  text-align: center;
  color: goldenrod;
  font-weight: bold;
  padding: 20px;
}
</style>
