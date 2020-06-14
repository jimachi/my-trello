<template>
  <div>
    <header>my trello</header>
    <main>
      <p class="info-line">All: {{ totalCardCount }} tasks</p>
      <div class="list-index">
        <list v-for="(item, index) in lists"
          :key="item.id"
          :title="item.title"
          :cards="item.cards"
          :listIndex="index"
          @change="movingCard"
        />
        <list-add />
      </div>
    </main>
  </div>
</template>

<script>
import List from './List'
import ListAdd from './ListAdd'

import { mapState } from 'vuex'

export default {
  components: {
    List,
    ListAdd
  },
  computed: {
    ...mapState(['lists']),
    totalCardCount () {
      return this.$store.getters.totalCardCount
    }
  },
  methods: {
    movingCard () {
      this.$store.dispatch('updateList', { lists: this.lists })
    }
  }
}
</script>
