<template>
  <div id="app">
    <img id="logo" alt="MLH Mascot" src="./assets/MLH-Mascots.png" />
    <h2 style="margin-top: 20px; margin-bottom: 20px">
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
      <div id="toDo" class="card col-sm-5" v-if="list.length > 0">
        <div class="card-body">
          <h5 class="card-title">To Do Items</h5>
          <ul
            class="list-group list-group-flush"
            v-for="item in list"
            :key="item.id"
          >
            <div class="row" style="text-align: left">
              <li class="list-group-item" v-if="!item.complete">
                <button
                  id="complete"
                  class="btn btn-primary col-sm-3"
                  v-on:click="markComplete(item)"
                >
                  Completed
                </button>
                {{ item.name }}
              </li>
            </div>
          </ul>
        </div>
      </div>
      <div id="done" class="card col-sm-5 offset-sm-1" v-if="list.length > 0">
        <div class="card-body">
          <h5 class="card-title">Finished Items</h5>
          <ul
            class="list-group list-group-flush"
            v-for="item in list"
            :key="item.id"
          >
            <div class="row" style="text-align: left">
              <li class="list-group-item" v-if="item.complete">
                <button
                  id="incomplete"
                  class="btn btn-danger col-sm-3"
                  v-on:click="markIncomplete(item)"
                >
                  Incomplete
                </button>
                {{ item.name }}
              </li>
            </div>
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
      this.newItem = "";
    },
    markComplete: function(item) {
      item.complete = true;
    },
    markIncomplete: function(item) {
      item.complete = false;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: bisque;
  width: 100%;
  height: 100vh;
}

#logo {
  margin-top: 15px;
  height: 200px;
  width: 200px;
  /* margin-left: 200px; */
}

/* #buttons {
  margin-top: 15px;
} */

#addItem {
  margin-left: 30px;
  margin-top: 15px;
}

#complete,
#incomplete {
  margin-right: 15px;
  font-weight: bold;
}

#toDo {
  margin-left: 25px;
  background-color: bisque;
  border-width: medium;
}

#done {
  background-color: bisque;
  border-width: medium;
}
</style>
