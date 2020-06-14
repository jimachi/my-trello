<template>
  <div>
    <header>my trello</header>
    <main>
      <p class="info-line">All: {{ totalCardCount }} tasks</p>
      <draggable class="list-index" :list="lists" @end="movingList">
        <list v-for="(item, index) in lists"
          :key="item.id"
          :title="item.title"
          :cards="item.cards"
          :listIndex="index"
          @change="movingCard"
        />
        <list-add />
      </draggable>
    </main>
  </div>
</template>

<script>
import draggable from 'vuedraggable'

import List from './List'
import ListAdd from './ListAdd'

import { mapState } from 'vuex'

export default {
  components: {
    draggable,
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
    },
    movingList () {
      this.$store.dispatch('updateList', { lists: this.lists })
    }
  }
}
</script>
