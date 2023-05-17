<template>
    <BoxComponent>
        <div class="columns">
            <div class="column is-7 task-text">
                {{ task.description || 'Task without description' }}
            </div>
            <div class="column text-task">
                <StopwatchComponent :timeInSeconds="task.timeInSeconds"/>
            </div>
        </div>
    </BoxComponent>
</template>

<script lang="ts">
import ITask from '@/interfaces/ITask'
import { defineComponent, PropType } from 'vue'
import BoxComponent from './BoxComponent.vue'
import StopwatchComponent from './StopwatchComponent.vue'

export default defineComponent({
    name: 'TaskComponent',
    components: {
        StopwatchComponent,
        BoxComponent,
    },
    props: {
        task: {
            type: Object as PropType<ITask>,
            required: true,
        },
    }
})
</script>

<style scoped>
.task-text {
    color: var(--primary-text);
}
</style>
