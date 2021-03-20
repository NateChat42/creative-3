<template>
<div class="wrapper">
  <div class="quests">
    <div class="quest" v-for="quest in quests" :key="quest.id">
      <div class="info">
        <h1>{{quest.name}}</h1>
        <h3>{{quest.location}}</h3>
        <p>{{quest.description}}</p>
      </div>
      <div class="reward">
        <h2>{{quest.reward}}</h2>
        <button class="auto" v-on:click="addToCart(quest)">Add to Quest Log</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'QuestList',
  props: {
    quests: Array
  },
  methods: {
      addToCart(quest) {
          this.$root.$data.cart.push(quest);
      }
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}

.quests {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.quest {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.info {
  background: #e86523;
  color: #000;
  padding: 10px 30px;
  min-height: 100px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info h3 {
  font-size: 12px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.reward {
  display: flex;
  font-size: 13px;
}

.reward h2 {
  color: yellow;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>