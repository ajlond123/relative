<template>
  <div class="page-manager">
      <div class="page-manager__header">
          <!-- Checkbox with label -->
      </div>

      <ul class="page-manager__list">
          <li
              v-for="page in orderedPages"
              :key="page.index"
              class="draggable"
              draggable="true"
              @dragstart="onDragstart($event, page)"
              @dragend="onDragend($event)"
              @dragover.prevent
              @dragenter.prevent
              @drop="onDrop($event, page)"
          >{{ page.title }}</li>
      </ul>

  </div>
</template>

<script>
import orderBy from 'lodash/orderBy';

export default {
    name: "PageManager",
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
    methods: {
        onDragstart(event, page) {
            event.dataTransfer.effectAllowed = 'move';
            event.target.style.opacity = '0.5';
            this.draggedItem = page;
        },
        onDragend(event) {
            event.target.style.opacity = 1;
        },
        onDrop(event, page) {
            const tempIndex = page.index;
            page.index = this.draggedItem.index;
            this.draggedItem.index = tempIndex
        },
    },
}
</script>

<style scoped>
    .page-manager {}

    .page-manager__header {}

    .page-manager__list {

    }

    .draggable {
        list-style: none;
        height: 122px;
        background: var(--white);
        padding: 16px;
    }
</style>
