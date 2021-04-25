<template>
    <div class="configurator">
        <img :src="panelSrc" class="" alt="">
        <img :src="panelExportSrc" class="configurator__export" alt="">
    </div>
</template>

<script>
import panelSrc from '/public/assets/panels/panel_doc-format.svg';
import panelExportSrc from '/public/assets/panels/export-short.svg';

export default {
    name: "Configurator",
    data() {
        return {
            panelSrc,
            panelExportSrc,
        };
    },
}
</script>

<style scoped>
    .configurator {
        height: calc(100vh - var(--headerHeight));
        position: relative;
    }

    .configurator__export {
        position: absolute;
        bottom: 0;
        left: 0;
    }
</style>
