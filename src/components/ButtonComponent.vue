<template>
    <button
        class="button"
        @click="this.buttonEvent"
        :disabled="isTimerOn"
    >
        <span class="icon">
            <i :class="buttonIcon"></i>
        </span>
        <span>{{ action }}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    props: {
        buttonEvent: {
            type: Function,
        },
        isTimerOn: {
            type: Boolean,
            default: false,
        },
        action: {
            type: String,
            default: '',
        }
    },
    computed: {
        buttonIcon () {
            return `fas fa-${this.action}`
        }
    }
})
</script>

<style>

</style>
