<template>
    <div id="app">
        <Header />
        <main class="container">
            <Sidebar position="left">
                <PageManager />
            </Sidebar>
            <Document />
            <Sidebar position="right">
                <Configurator />
            </Sidebar>
        </main>
    </div>
</template>

<script>

import Header from "@/components/Header";
import Sidebar from "@/components/Sidebar";
import Document from "@/components/Document";
import PageManager from "@/components/PageManager";
import Configurator from "@/components/Configurator";

export default {
    name: 'App',
    components: {
        Configurator,
        PageManager,
        Document,
        Sidebar,
        Header,
    },
}
</script>

<style>
@import '~normalize.css';
@import 'styles/index.css';

.container {
    display: grid;
    grid-template-columns: 246px auto 246px;
    width: 100%;
    height: calc(100vh - var(--headerHeight));
    overflow: hidden;
}
</style>
