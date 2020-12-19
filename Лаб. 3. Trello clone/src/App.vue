<template>
  <div class="row container align-center justify-center">
    <div class="flex-row justify-center">
      <div class="cole-3" v-for="list in lists" :key="list.index" style="margin: 0 30px">
        <h3 style="color:white"> {{list.title}}</h3>
        <button type="button" @click="add(list.dataArray)">Add</button>
        <button type="button" @click="deleteLast(list.dataArray)">Delete</button>
        <draggable
          class="list-group"
          :list="list.dataArray"
          group="people"
          @change="log"
          itemKey="name"
        >
          <template #item="{ element, index }">
            <div class="list-group-item" style="color:white">{{ element.name }} {{ index }}</div>
          </template>
        </draggable>
      </div>
      <rawDisplayer class="col-3" v-for="list in lists" :key="list.index" :value="list.dataArray"/>
    </div>
  </div>
</template>
<script>
import draggable from "vuedraggable";
export default {
  name: "two-lists",
  display: "Two Lists",
  order: 1,
  components: {
    draggable
  },
  data() {
    return {
      lists: [
        {
          dataArray: [
            { name: "Task", id: 1 },
            { name: "Task", id: 2 },
            { name: "Task", id: 3 },
            { name: "Task", id: 4 }
          ],
          id: 1,
          title: 'Backlog'
        },
        {
          dataArray: [
            { name: "Task", id: 1 },
            { name: "Task", id: 2 },
            { name: "Task", id: 3 },
            { name: "Task", id: 4 }
          ],
          id: 2,
          title: 'In Dev Sprint'
        },
        {
          dataArray: [
            { name: "Task", id: 1 },
            { name: "Task", id: 2 },
            { name: "Task", id: 3 },
            { name: "Task", id: 4 }
          ],
          id: 3,
          title: 'Done'
        }
      ]
    };
  },
  methods: {
    add: function(list) {
      list.push({ name: "Task" });
    },
    deleteLast: function(list) {
      list.pop()
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.flex-row {
  display: flex;
  flex-direction: row
}
.justify-center {
  display: flex;
  justify-content: center
}
.container {
  height: 100vh;
  background: url(../public/images/background.jpg) no-repeat;
  background-size: cover;
}
.dnd-list {
  margin: auto
}
</style>
