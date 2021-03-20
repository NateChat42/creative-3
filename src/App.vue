<template>
<div id="app">
  <div id="menu">
    <div id="brand">
      <router-link to="/">
        <img src="/images/logo.png">
      </router-link>
    </div>
    <div id="side">
      <router-link to="/addquest">
        <div class="menu-item plus">
          <img class="plus-img" src="/images/plus-removebg-preview.png">
          <p>Manage Quests</p>
        </div>
      </router-link>
      <router-link to="/cart">
        <div class="menu-item">
          <img src="/images/quest.png">
          <p>{{cartSize}} quests</p>
        </div>
      </router-link>
    </div>
  </div>
  <router-view />
</div>
</template>

<script>
export default {
  computed: {
    cartSize() {
      try {
      return this.$root.$data.cart.length;
      } catch (error) {
        return 0;
      }
    }
  }
}
</script>


<style>
* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;
  background: #3a3939;
}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 300px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-item p {
  margin: 0px;
}

.browse {
  margin-right: 50px;
}

.plus {
  margin-right: 50px;
}

.plus-img {
  margin-left: 30px;
}

</style>