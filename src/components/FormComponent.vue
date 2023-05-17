<template>
    <div class="box form">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Form to create a new task.">
                <input 
                    type="text" 
                    class="input" 
                    placeholder="Which task do you want to start?"
                    v-model="description"
                >
            </div>    
            <div class="column">
                <TimerComponent @onTimerEnd="finishTask"/>
            </div>
        </div>    
    </div>    
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TimerComponent from './TimerComponent.vue'

export default defineComponent({
    name: 'FormComponent',
    emits: ['onSaveTask'],
    data () {
        return {
            description: ''
        }
    },
    components: {
        TimerComponent,
    },
    methods: {
        finishTask (timeSpent: number) : void {
            this.$emit('onSaveTask', {
                timeInSeconds: timeSpent,
                description: this.description,
            })
            this.description = ''
        }
    }
})
</script>

<style>
.form {
    color: var(--primary-text);
    background-color: var(--primary-background);
}
</style>