<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select('United States')" href="#" class="pure-menu-link">United States</a></li>
      <li class="pure-menu-item"><a @click="select('Canada')" href="#" class="pure-menu-link">Canada</a></li>
      <li class="pure-menu-item"><a @click="select('Mexico')" href="#" class="pure-menu-link">Mexico</a></li>
      <li class="pure-menu-item"><a @click="select('Brazil')" href="#" class="pure-menu-link">Brazil</a></li>
    </ul>
  </div>
  <QuestList :quests="quests" />
</div>
</template>

<script>
import QuestList from "../components/QuestList.vue"
export default {
  name: 'Browse',
  components: {
    QuestList
  },
  data() {
    return {
      location: '',
    }
  },
  computed: {
    quests() {
      return this.$root.$data.quests.filter(quest => quest.location === this.location);
    }
  },
  methods: {
    select(location) {
      this.location = location;
    }
  }
}
</script>