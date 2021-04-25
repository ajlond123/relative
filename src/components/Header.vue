<template>
    <header class="header">
        <h1 class="heading heading--sm">Export Insight Cards</h1>
        <!-- Zoom -->
        <!-- Hide sidebars -->
        <!-- Close -->
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header {
        display: flex;
        height: var(--headerHeight);
        align-content: center;
        align-items: center;
        background: var(--white);
        padding: 0 var(--defaultSpacing);
        border-bottom: 1px solid var(--mid-grey);
    }
</style>
