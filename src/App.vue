<template>
  <main class="columns is-gapless is-multline" :class="{ 'dark-mode': isDarkMode }">
    <div class="column is-one-quarter">
      <SideBarComponent @onThemeChanged="changeThemeMode"/>
    </div>
    <div class="column is-three-quarter content">
      <FormComponent 
        @onSaveTask="saveTask"
      />
      <div class="lista">
        <TaskComponent 
          v-for="(task, index) in taskList"
          :key="index"
          :task="task"
        />
        <BoxComponent v-if="isListEmpty">
          You're not productive today =(
        </BoxComponent>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import SideBarComponent from './components/SideBarComponent.vue'
import FormComponent from './components/FormComponent.vue'
import TaskComponent from './components/TaskComponent.vue'
import BoxComponent from './components/BoxComponent.vue'
import ITask from './interfaces/ITask.js'

import { defineComponent } from 'vue';


export default defineComponent({
  name: 'App',
  components: {
    SideBarComponent,
    FormComponent,
    TaskComponent,
    BoxComponent,
  },
  data () {
    return {
      taskList: [] as ITask [],
      isDarkMode: false
    }
  },
  computed: {
    isListEmpty () : boolean {
      return this.taskList.length === 0
    }
  },
  methods: {
    saveTask (task: ITask) {
      this.taskList.push(task)
    },
    changeThemeMode (isDarkMode : boolean) {
      this.isDarkMode = isDarkMode
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --primary-background: #fff;
  --secondary-background: #FAF0CA;
  --primary-text: #000; 
}
main.dark-mode {
  --primary-background: #2b2d42;
  --secondary-background: #0d3b66;
  --primary-text: #ddd; 
}
.content {
  background-color: var(--primary-background);
}
</style>