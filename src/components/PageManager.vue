<template>
  <div class="page-manager">
      <header class="page-manager__header">
          <Checkbox
              label="Export all"
              @checked="exportAll"
          />
      </header>

      <div class="page-manager__pages">
          <ul>
              <draggable
                  v-model="pages"
                  ghost-class="page--ghost"
                  chosen-class="page--chosen"
                  drag-class="page--drag"
              >
                  <li
                      v-for="(page, index) in pages"
                      :key="page.index"
                      class="page"
                  >
                      <div class="page__inner">
                          <Checkbox
                              @checked="selectPage(page, $event)"
                              :checked="page.checked"
                          />
                          <div class="page__box" />
                          <p class="text">{{ title(index, page.title) }}</p>
                      </div>
                  </li>
              </draggable>
          </ul>
      </div>

      <footer class="page-manager__footer">
          <p class="text">
              <strong>Page numbers</strong>
          </p>
          <svg width="26" height="16" viewBox="0 0 26 16" fill="none" xmlns="http://www.w3.org/2000/svg">
              <rect y="5" width="26" height="6" rx="3" fill="#E2E2E2"/>
              <circle cx="18" cy="8" r="7.5" fill="#55BD00" stroke="white"/>
          </svg>
      </footer>
  </div>
</template>

<script>
import draggable from 'vuedraggable';

import Checkbox from "@/components/Checkbox";

export default {
    name: "PageManager",
    components: {
        draggable,
        Checkbox
    },
    data() {
        return {
            allPagesSelected: false,
            pages: [
                {
                    title: 'Friends',
                    index: 1,
                    checked: false,
                },
                {
                    title: 'Spoken interjections',
                    index: 2,
                    checked: false,
                },
                {
                    title: 'Exaggeration',
                    index: 3,
                    checked: false,
                },
                {
                    title: 'First / second person',
                    index: 4,
                    checked: false,
                },
                {
                    title: 'Do what you love',
                    index: 5,
                    checked: false,
                },
                {
                    title: 'No food guilt',
                    index: 6,
                    checked: false,
                },
            ],
        };
    },
    methods: {
        title(index, title) {
            return `${index + 1}. ${title}`;
        },
        exportAll() {
            this.pages.forEach((page) => {
                page.checked = !this.allPagesSelected;
            });

            this.allPagesSelected = !this.allPagesSelected;
        },
        selectPage(page, event) {
            page.checked = event.$event.target.checked;
        },
    },
}
</script>

<style>
    :root {
        --border: 1px solid var(--mid-grey);
    }
</style>

<style scoped>
    /* Page manager */
    .page-manager {
        background: var(--light-grey);
    }

    .page-manager__header {
        border-bottom: var(--border);
        padding: 12px var(--defaultSpacing);
    }

    .page-manager__footer {
        display: flex;
        justify-content: space-between;
        border-top: var(--border);
        border-bottom: var(--border);
        background: var(--white);
        padding: var(--defaultSpacing);
    }

    /* Page */
    .page {
        position: relative;
        list-style: none;
        height: 122px;
        background: var(--white);
        padding: var(--defaultSpacing);
        border-right: var(--border);
        border-bottom: var(--border);
        width: calc(100% - 14px);
        cursor: move;
        transition: background 0.1s ease-in 25ms;
    }

    .page__inner {
        display: flex;
        flex-wrap: wrap;
    }

    .page-manager .page:last-child {
        border-bottom: none;
    }

    .page--ghost {
        background: transparent;
    }

    .page--ghost .page__inner {
        visibility: hidden;
    }

    .page--ghost:before {
        content: '';
        position: absolute;
        top: 16px;
        left: 16px;
        background: var(--green);
        height: calc(100% - 32px);
        width: 4px;
    }

    .page--drag {
        opacity: 1 !important;
        border: 1px dashed var(--green);
        background: white;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
        border-radius: 2px;
    }

    .page--drag .page__box {
        border: 1px solid var(--green);
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
