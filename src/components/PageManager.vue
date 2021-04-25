<template>
  <div class="page-manager">
      <div class="page-manager__header">
          <Checkbox
              label="Export all"
              @checked="exportAll"
          />
      </div>

      <div class="page-manager__pages">
          <ul ref="pages">
              <li
                  v-for="(page, index) in orderedPages"
                  :key="page.index"
                  class="page"
                  draggable="true"
                  @dragstart="onDragstart($event, page)"
                  @dragend="onDragend($event)"
                  @drag="onDrag($event)"
                  @dragover.prevent
                  @dragenter.prevent
                  @drop="onDrop($event, page)"
              >
                  <Checkbox @checked="selectPage" />
                  <div class="page__box" />
                  <p class="text">{{ title(index, page.title) }}</p>
              </li>
          </ul>

          <ul class="cloned-pages" ref="clones" />
      </div>
  </div>
</template>

<script>
import orderBy from 'lodash/orderBy';
import Checkbox from "@/components/Checkbox";

export default {
    name: "PageManager",
    components: {Checkbox},
    data() {
        return {
            draggedItem: null,
            pages: [
                {
                    title: 'Friends',
                    index: 1,
                },
                {
                    title: 'Spoken interjections',
                    index: 2,
                },
                {
                    title: 'Exaggeration',
                    index: 3,
                },
                {
                    title: 'First / second person',
                    index: 4,
                },
                {
                    title: 'Do what you love',
                    index: 5,
                },
                {
                    title: 'No food guilt',
                    index: 6,
                },
            ],
        };
    },
    computed: {
        orderedPages() {
            return orderBy(this.pages, 'index');
        },
    },
    mounted() {
        this.createClones();
    },
    methods: {
        title(index, title) {
            return `${index + 1}. ${title}`;
        },
        isDragged(page) {
            return this.draggedItem === page;
        },
        onDragstart(event, page) {
            event.dataTransfer.effectAllowed = 'move';
            this.draggedItem = page;
        },
        onDragend(event) {
            event.target.style.opacity = '1';
            event.target.classList.remove('is-dragged');
            this.draggedItem = null;
        },
        onDrop(event, page) {
            const tempIndex = page.index;
            page.index = this.draggedItem.index;
            this.draggedItem.index = tempIndex
        },
        onDrag(event) {
            console.log(event);
        },
        exportAll(event) {
            console.log('export all', event.$event.target.checked);
        },
        selectPage(event) {
            console.log('select page', event.$event.target.checked);
        },
        generateKey(index) {
            return index + Math.random();
        },
        createClones() {
            const pages = this.$refs.pages.children;
            const clonesElem = this.$refs.clones;

            [...pages].forEach((page) => {
                let clone;
                const position = page.getBoundingClientRect();

                clone = page.cloneNode(true);
                clone.classList.add('page--cloned');

                clone.style.cssText = `
                    left: ${position.left}px;
                    top: ${position.top}px;
                    width: ${position.width}px
                `;

                clonesElem.appendChild(clone);
            });
        },
    },
}
</script>


<style>
    :root {
        --pageBorder: 1px solid var(--mid-grey);
    }
</style>

<style scoped>
    /* Page manager */
    .page-manager {}

    .page-manager__header {
        padding: var(--defaultSpacing);
        background: var(--light-grey);
    }

    .page-manager__list {

    }

    /* Page */

    .page {
        display: flex;
        flex-wrap: wrap;
        list-style: none;
        height: 122px;
        background: var(--white);
        padding: var(--defaultSpacing);
        border-right: var(--pageBorder);
        border-bottom: var(--pageBorder);
        width: calc(100% - 14px);
    }

    .page.is-dragged {
        visibility: visible;
        position: absolute;
        width: 232px;
        height: 122px;
        z-index: 100;
        opacity: 1;
    }

    .page--cloned {
        display: block;
        position: absolute;
        z-index: 1;
        visibility: hidden;
    }

    .drag-marker {
        position: relative;
        height: 50px;
        width: 5px;
        border-left: 2px solid var(--green);
        margin: 0 0 0.75rem 0;
        z-index: 6;
    }

    .page .text {
        width: 100%;
        text-indent: 34px; /* checkbox size + grid-gap (18px + 16px)  */
    }

    .page__box {
        background: var(--grey);
        width: 110px;
        height: 62px;
        margin-bottom: var(--defaultSpacing);
    }
</style>
