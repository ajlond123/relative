<template>
    <label class="checkbox">
        <span class="checkbox__input">
            <input
                type="checkbox"
                name="checkbox"
                :checked="checked"
                @change="$emit('checked', { $event })"
            >
            <span class="checkbox__control">
                <svg version="1.1" xmlns="http://www.w3.org/2000/svg" width="18" height="16" viewBox="0 0 18 16">
                    <title>tick</title>
                    <path fill="#55bd00" d="M17.795 0.508c-0.327-0.325-0.77-0.508-1.231-0.508s-0.904 0.183-1.231 0.508l-8.644 8.644-3.702-3.702c-0.162-0.164-0.355-0.294-0.568-0.382s-0.441-0.134-0.672-0.134-0.459 0.046-0.672 0.134c-0.213 0.089-0.406 0.219-0.568 0.382-0.325 0.327-0.508 0.77-0.508 1.231s0.183 0.904 0.508 1.231l3.702 3.702 2.48 2.427 11.088-11.088c0.322-0.324 0.505-0.762 0.508-1.219s-0.173-0.897-0.49-1.226z"></path>
                </svg>
            </span>
        </span>
        <span
            class="checkbox__label text"
            v-if="label !== ''"
        >
            <strong>{{ label }}</strong>
        </span>
    </label>
</template>

<script>
export default {
    name: "Checkbox",
    props: {
        label: {
            type: String,
            required: false,
            default: '',
        },
        checked: {
            type: Boolean,
            required: false,
            default: false,
        }
    },
}
</script>

<style>
:root {
    --checkboxSize: 18px;
}
</style>

<style scoped>
.checkbox {
    display: grid;
    grid-template-columns: min-content auto;
    grid-gap: var(--defaultSpacing);
    cursor: pointer;
}

.checkbox__control {
    display: inline-grid;
    width: var(--checkboxSize);
    height: var(--checkboxSize);
    border-radius: 2px;
    border: 1px solid var(--black);
    align-content: center;
    justify-content: center;
    transition: border-color 0.1s ease-in 25ms;
}

.checkbox__control svg {
    transition: opacity 0.1s ease-in 25ms;
    opacity: 0;
    width: 8px;
    height: 8px;
    fill: var(--green);
}

.checkbox__input {
    display: grid;
    grid-template-areas: "checkbox";
}

.checkbox__input  > * {
    grid-area: checkbox;
}

.checkbox__input input {
    opacity: 0;
    width: var(--checkboxSize);
    height: var(--checkboxSize);
    cursor: pointer;
}

.checkbox__input input:checked + .checkbox__control {
    border-color: var(--green);
}

.checkbox__input input:checked + .checkbox__control svg {
    opacity: 1;
}

.checkbox__label {
    display: flex;
    align-items: center;
}
</style>
