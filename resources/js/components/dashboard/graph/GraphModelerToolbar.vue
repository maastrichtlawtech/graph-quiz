<template>

    <div class="toolbar ">
        <div class="toolbar-item">
            <button @click="item_use()"><i class="las la-play-circle"></i>Use</button>
        </div>
        <div class="toolbar-item">
            <button @click="item_reload()"><i class="las la-sync"></i>Reload</button>
        </div>
        <div class="toolbar-item">
            <button @click="item_save()"><i class="las la-cloud-upload-alt"></i>Save</button>
        </div>
        <div class="toolbar-item">
            <button @click="item_undo()"><i class="las la-undo"></i>Undo</button>
        </div>
        <div class="toolbar-item">
            <button @click="item_redo()"><i class="las la-redo"></i>Redo</button>
        </div>
    </div>

</template>

<script>
    // https://github.com/antvis/X6/blob/master/sites/x6-sites-demos/packages/tutorial/basic/dnd/dnd/src/app.tsx

    import { Dom, Addon } from '@antv/x6';

    const { Dnd } = Addon;

    export default {

        props: {
            graph: {
                type: Object,
                required: true,
            },
            remote_graph_data_reload: {
                type: Function,
            },
            remote_graph_data: {
                type: Object,
            },
            local_save: {
                type: Function,
            },
        },

        mounted() {

        },

        data() {
            return {
            }
        },

        methods: {
            item_use() {
                window.open(route('graph.show', [this.remote_graph_data.graph.id]), '_blank');
            },
            item_reload() {
                this.remote_graph_data_reload()
            },
            item_save() {
                this.local_save()
            },
            item_undo() {
                this.graph.undo();
            },
            item_redo() {
                this.graph.redo();
            },
        },

    }
</script>

<style lang="scss">
    .toolbar {

        @apply flex p-2;

        .toolbar-item button {
            @apply bg-white border border-gray-300 text-gray-800 px-3 py-1  mr-2 rounded-md;

            @apply flex items-center;

            i {
                @apply mr-2 text-lg leading-none;
            }

            &:hover {
                @apply bg-gray-200 border-gray-400 cursor-pointer;
            }
        }

    }

</style>
