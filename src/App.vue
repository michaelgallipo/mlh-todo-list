<template>
  <div id="app">
    <img id="logo" alt="MLH Mascot" src="./assets/MLH-Mascots.png" />
    <h2 style="margin-top: 15px; margin-left: 185px">
      Internet Hippo's To Do App
    </h2>
    <div class="col-sm-6">
      <input
        type="text"
        class="form-control"
        v-model="newItem"
        maxlength="50"
        placeholder="New To-Do Item"
        style="margin-left: 20px"
      />
    </div>
    <div id="buttons" class="row">
      <button
        id="addItem"
        class="btn btn-primary col-sm-2"
        v-on:click="addItem()"
      >
        Add New Item
      </button>
    </div>
    <br />
    <div class="row">
      <div class="card col-sm-4" v-if="list.length > 0">
        <div class="card-body">
          <h5 class="card-title">To Do Items</h5>
          <ul
            class="list-group list-group-flush"
            v-for="item in list"
            :key="item.id"
          >
            <li class="list-group-item" v-if="!item.complete">
              {{ item.name }}
              <button
                class="btn btn-primary col-sm-5 offset sm-2"
                v-on:click="markComplete(item)"
              >
                Completed
              </button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  // components: {
  //   HelloWorld
  // }
  data: function() {
    return {
      list: [],
      newItem: ""
    };
  },
  methods: {
    addItem: function() {
      let id = this.list.length + 1;
      let item = { id: id, name: this.newItem, complete: false };
      this.list.push(item);
      console.log(this.list);
    },
    markComplete: function(item) {
      item.complete = true;
    },
    markIncomplete: function(item) {
      this.item.complete = false;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

#logo {
  height: 200px;
  width: 200px;
  margin-left: 200px;
}

#buttons {
  margin-top: 15px;
}

#addItem {
  margin-left: 20px;
}
</style>
