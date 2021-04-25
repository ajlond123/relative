<template>
    <div class="configurator">
        <img :src="panelSrc" alt="Document format UI component">

        <div
            v-for="(section, index) in ['Orientation', 'Header', 'Footer']"
            :key="index"
            class="configurator__section"
        >
            <p class="text">
                <strong>{{ section }}</strong>
            </p>
            <svg width="26" height="16" viewBox="0 0 26 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect y="5" width="26" height="6" rx="3" fill="#E2E2E2"/>
                <circle cx="18" cy="8" r="7.5" fill="#55BD00" stroke="white"/>
            </svg>
        </div>

        <img :src="panelExportSrc" class="configurator__export" alt="File export UI component">
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
            sections: [
                'Orientation',

            ]
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

    .configurator__section {
        display: flex;
        justify-content: space-between;
        padding: var(--defaultSpacing);
        background: var(--light-grey);
        border-bottom: var(--border);
    }
</style>
