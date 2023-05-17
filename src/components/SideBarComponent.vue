<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="Alura Tracker Logo">
        </h1>
        <button class="button" @click="changeThemeMode">
          Dark Mode
        </button>
    </header>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
    name: 'SideBar',
    emits: ['onThemeChanged'],
    data () {
      return {
        isDarkMode: false,
      }
    },
    methods: {
      changeThemeMode () {
        this.isDarkMode = !this.isDarkMode
        this.$emit('onThemeChanged', this.isDarkMode)
      }
    }
  })
</script>

<style scoped>
header {
  padding: 2rem;
  background-color: #0d3b66;
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: space-between;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>

