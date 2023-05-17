<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <StopwatchComponent :timeInSeconds="timeInSeconds" />
        <ButtonComponent 
            :buttonEvent="startCounting"
            :isTimerOn="isTimerOn"
            action="play"
        />
        <ButtonComponent 
            :buttonEvent="stopCounting"
            :isTimerOn="!isTimerOn"
            action="stop"
        />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ButtonComponent from './ButtonComponent.vue'
import StopwatchComponent from './StopwatchComponent.vue'

export default defineComponent({
    name: 'TimerComponent',
    emits: ['onTimerEnd'],
    components: {
        StopwatchComponent,
        ButtonComponent,
    },
    data () {
        return {
            timeInSeconds: 0,
            timer: 0,
            isTimerOn: false,
        }
    },
    methods: {
        startCounting () {
            this.timer = setInterval(() => {
                this.timeInSeconds+=1
            }, 1000)
            this.isTimerOn = true
        },
        stopCounting () {
            clearInterval(this.timer)
            this.isTimerOn = false
            this.$emit('onTimerEnd', this.timeInSeconds)
            this.timeInSeconds = 0
        }
    }
})
</script>

<style>

</style>

