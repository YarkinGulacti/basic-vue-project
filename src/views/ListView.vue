<script lang="ts">
    export default {
        data() {
            return {
                items: new Array<{
                    key: string;
                    value: any;
                }>(),
                key: "",
                value: undefined,
            };
        },
        methods: {
            addItem(item: { key: string; value: any }) {
                this.items.push(item);
            },
            deleteItem(index: number) {
                this.items = [...this.items.slice(0, index), ...this.items.slice(index + 1)];
            },
        },
    };
</script>
<template>
    <div>
        <h1 style="text-align: center">List View</h1>
        <hr />
        <div>
            <label for="key">Key</label>
            <input
                id="key"
                v-model="key"
                placeholder="Key of item..."
            />
        </div>
        <div>
            <label for="value">Value</label>
            <input
                id="value"
                v-model="value"
                placeholder="Value of item..."
            />
        </div>
        <button
            type="button"
            @click="addItem({ key, value })"
        >
            Add Item
        </button>
        <hr />
        <ul>
            <li
                v-for="(item, index) in items"
                :key="item.key"
            >
                <code style="margin-right: 5px">Key: {{ item.key }}</code>
                <code style="margin-right: 5px">Value: {{ item.value }}</code>
                <button @click="deleteItem(index)">Delete Item</button>
            </li>
        </ul>
    </div>
</template>
