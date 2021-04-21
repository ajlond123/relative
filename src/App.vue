<template>
    <div id="app">
        <Header />
        <main class="container" :style="{ height: deviceHeight }">
            <Sidebar position="left">
                <PageEditor />
            </Sidebar>
            <Page />
            <Sidebar position="right">
                <Configurator />
            </Sidebar>
        </main>
    </div>
</template>

<script>

import Header from "@/components/Header";
import Sidebar from "@/components/Sidebar";
import Page from "@/components/Page";
import PageEditor from "@/components/PageEditor";
import Configurator from "@/components/Configurator";

export default {
    name: 'App',
    components: {
        Configurator,
        PageEditor,
        Page,
        Sidebar,
        Header,
    },
    data() {
        return {
            deviceHeight: '',
        };
    },
    methods: {
        setFrameHeight() {
            if (window.innerHeight) {
                return `${(window.innerHeight - 50)}px` // frame height - header height
            }

            return '100vh'
        }
    },
    mounted() {
        this.deviceHeight = this.setFrameHeight();
    }
}
</script>

<style>
@import '~normalize.css';
@import 'styles/index.css';

.container {
    display: grid;
    grid-template-columns: 246px auto 246px;
    width: 100%;
}
</style>
