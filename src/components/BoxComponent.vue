<template>
    <div class="box has-text-weight-bold">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'BoxComponent'
})
</script>

<style scoped>
.box {
    color: var(--primary-text);
    background-color: var(--secondary-background);
}
</style>
