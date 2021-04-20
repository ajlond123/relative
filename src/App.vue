<template>
    <div id="app">
        <PageEditor></PageEditor>
    </div>
</template>

<script>
import PageEditor from "@/components/PageEditor";

export default {
    name: 'App',
    components: {
        PageEditor
    }
}
</script>

<style>
@import '~normalize.css';
@import 'styles/index.css';
</style>
