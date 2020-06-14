<template>
  <form :class="classList" @submit.prevent="addList">
    <input type="text"
      v-model="title"
      class="text-input"
      placeholder="Add new List"
      @focusin="startEditing"
      @focusout="finishEditing"
    >
    <button type="submit"
      class="add-button"
      v-if="isEdting || titleExists"
    >Add</button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      title: '',
      isEdting: false 
    }
  },
  computed: {
    classList () {
      const classList = ['addlist']
      if (this.isEdting) classList.push('active')

      if (this.titleExists) classList.push('addable')

      return classList
    },
    titleExists () {
      return this.title.length > 0
    }
  },
  methods: {
    addList () {
      this.$store.dispatch('addlist', { title: this.title })
      this.title = ''
    },
    startEditing () {
      this.isEdting = true
    },
    finishEditing () {
      this.isEdting = false
    }
  }
}
</script>