<template>
  <div>
    <h1 class="header" v-show="this.$root.$data.cart.length === 0">Quest Log is empty</h1>

    <div class="wrapper">
      <div class="quests">
        <div class="quest" v-for="quest in cartArray" :key="quest.id">
          <div class="info">
            <h1>{{ quest.name }}</h1>
            <p>{{ quest.location }}</p>
          </div>
          <div class="image">
            <img :src="'/images/quests/' + quest.image" />
          </div>
          <div class="reward">
            <h2>{{ quest.reward }}</h2>
            <button class="auto" v-on:click="removeFromCart(quest)">
              Remove from Quest Log
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: {
    cart: Array,
  },
  computed: {
    cartArray() {
      return this.$root.$data.cart;
    }
  },
  methods: {
    removeFromCart(quest) {
      this.$root.$data.cart.splice(this.$root.$data.cart.indexOf(quest),1);
    }
  },
};
</script>

<style scoped>
.header {
  text-align: center;
}

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
  background: green;
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