<template>
    <div class="document">
        <div class="document__canvas" />
    </div>
</template>

<script>
export default {
    name: "Document"
}
</script>

<style scoped>
    .document {
        display: flex;
        align-content: center;
        justify-content: center;
        align-items: center;
        background: var(--light-grey);
    }

    .document__canvas {
        background: var(--canvas);
        width: 100%;
        max-width: 521px;
        height: 742px;
    }
</style>
