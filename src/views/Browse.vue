<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select('Kalimdor')" href="#" class="pure-menu-link">Kalimdor</a></li>
      <li class="pure-menu-item"><a @click="select('Eastern Kingdoms')" href="#" class="pure-menu-link">Eastern Kingdoms</a></li>
      <li class="pure-menu-item"><a @click="select('Northrend')" href="#" class="pure-menu-link">Northrend</a></li>
      <li class="pure-menu-item"><a @click="select('Pandaria')" href="#" class="pure-menu-link">Pandaria</a></li>
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