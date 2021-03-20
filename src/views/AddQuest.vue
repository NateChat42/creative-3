<template>
  <div class="addquest">
    <div class = "heading">
        <h2>Add a Quest!</h2>
    </div>
    <div class="add">
      <div class="form">
        <input v-model="name" placeholder="Name" />
        <p></p>
        <input v-model="location" placeholder="Location" />
        <p></p>
        <input v-model="reward" placeholder="Reward" />
        <p></p>
        <input v-model="description" placeholder="Description" />
        <p></p>
        <button @click="addQuest">Add Quest</button>
      </div>
      <div v-if="addItem">
        <h2>{{ addItem.name }}</h2>
        <p>{{ addItem.description }}</p>
        <p>{{ addItem.reward }}</p>
        <p>{{ addItem.location }}</p>
      </div>
    </div>
    <br />

    <div class = "heading">
        <h2>Edit or Delete a Quest!</h2>
    </div>
    <div class="edit">
      <div class="form">
        <input v-model="findName" placeholder="Search" />
        <div class="suggestions" v-if="suggestions.length > 0">
          <div class="suggestion" v-for="s in suggestions" :key="s.id" @click="selectItem(s)"          >
            {{s.name}}
          </div>
        </div>
      </div>
      <div v-if="findItem">
        <input v-model="findItem.name" />
        <p></p>
        <input v-model="findItem.location" />
        <p></p>
        <input v-model="findItem.reward" />
        <p></p>
        <input v-model="findItem.description" />
        <p></p>
      </div>
      <div v-if="findItem">
        <button @click="editItem(findItem)">Edit</button>
        <button @click="deleteItem(findItem)">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddQuest",
  data() {
    return {
      name: "",
      reward: "",
      description: "",
      location: "",
      addItem: null,
      items: [],
      findName: "",
      findItem: null,
    };
  },
  computed: {
    suggestions() {
      let items = this.items.filter((item) =>
        item.name.toLowerCase().startsWith(this.findName.toLowerCase())
      );
      return items.sort((a, b) => a.name > b.name);
    },
  },
  created() {
    this.getItems();
  },
  methods: {
    addQuest() {
      let newQuest = {
        name: this.name,
        description: this.description,
        reward: this.reward,
        location: this.location,
      };
      this.$root.$data.quests.push(newQuest);
      this.addItem = newQuest.data;
    },
    getItems() {
      this.items = this.$root.$data.quests;
    },
    selectItem(item) {
      this.findTitle = "";
      this.findItem = item;
    },
    deleteItem(item) {
      this.$root.$data.quests.splice(this.$root.$data.quests.indexOf(item), 1);
      this.findItem = null;
      this.getItems();
    },
    editItem(item) {
      let questIndex = this.$root.$data.quests.indexOf(item);
      this.$root.$data.quests[questIndex] = item;
      this.findItem = null;
      this.getItems();
      // return true;
    },
  },
};
</script>

<style scoped>

.addquest {
    margin-bottom: 30px;
}

.heading {
    text-align: center;
}

.add,
.edit {
  display: flex;
  justify-content: center;
}

input,
textarea,
select,
button {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  font-size: 1em;
}

.form {
  margin-right: 50px;
}

.suggestions {
  width: 200px;
  border: 1px solid #ccc;
}

.suggestion {
    min-height: 20px;
    color: white;
}

.suggestion:hover {
    background-color: #5bdeff;
    color: black;
}
</style>