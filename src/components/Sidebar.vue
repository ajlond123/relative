<template>
    <div
        class="sidebar"
        :class="`sidebar--${position}`"
    >
        <slot />
    </div>
</template>

<script>
export default {
    name: "Sidebar",
    props: {
        position: {
            type: String,
            required: true,
        },
    },
}
</script>

<style scoped>
    .sidebar {}

    .sidebar--left {
        border-right: 1px solid var(--mid-grey);
    }

    .sidebar--right {
        border-left: 1px solid var(--mid-grey);
    }
</style>
