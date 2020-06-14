<template>
  <div>
    <header>my trello</header>
    <main>
      <p class="info-line">All: 0 tasks</p>
      <list-add />
    </main>
  </div>
</template>

<script>
import ListAdd from './ListAdd'

export default {
  components: {
    ListAdd
  }
}
</script>
