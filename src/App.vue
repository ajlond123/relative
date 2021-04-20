<template>
    <div id="app">
        <Header/>
        <PageEditor></PageEditor>
    </div>
</template>

<script>
import PageEditor from "@/components/PageEditor";
import Header from "@/components/Header";

export default {
    name: 'App',
    components: {
        Header,
        PageEditor
    }
}
</script>

<style>
@import '~normalize.css';
@import 'styles/index.css';
</style>
