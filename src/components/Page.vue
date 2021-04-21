<template>
    <div class="page">
        <div class="page__canvas">

        </div>
    </div>
</template>

<script>
export default {
    name: "Page"
}
</script>

<style scoped>
    .page {
        display: flex;
        align-content: center;
        justify-content: center;
        align-items: center;
        background: var(--panel-backdrop);
    }

    .page__canvas {
        background: var(--canvas);
        width: 100%;
        max-width: 521px;
        height: 742px;
    }
</style>
