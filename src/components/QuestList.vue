<template>
<div class="wrapper">
  <div class="quests">
    <div class="quest" v-for="quest in quests" :key="quest.id">
      <div class="info">
        <h1>{{quest.name}}</h1>
        <p>{{quest.location}}</p>
      </div>
      <div class="image">
        <img :src="'/images/quests/'+quest.image">
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

.quest img {
  border: 2px solid #333;
  height: 250px;
  width: 200px;
  object-fit: cover;
}

.quest .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #e86523;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.reward {
  display: flex;
  font-size: 13px;
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