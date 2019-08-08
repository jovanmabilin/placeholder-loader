<template>
    <div class="m-0 p-0">
        <template v-if="isLoading">
            <component :is="template" :row="row" :column="column"></component>    
        </template>
        <template v-else>
            <slot></slot>
        </template>
    </div>
</template>

<script>
    /**
     * CRM Loader
     * 
     * Props: template, row, column
     * Templates:
     *          - imgBodyVertical
     *          - imgBodyHorizontal
     *          - list
     *          - bulletList
     */
    import list from './templates/list';
    import bulletList from './templates/bulletList';
    import imgBodyHorizontal from './templates/imgBodyHorizontal';
    import imgBodyVertical from './templates/imgBodyVertical';
    import box from './templates/box';
    import tableList from './templates/tableList';
    export default {
        props: {
            template: {
                type: String,
                default: 'list',
            },
            row: {
                type: Number,
                default: 5,
            },
            column: {
                type: Number,
                default: 1
            },
            isLoading: {
                type: Boolean,
                default: false,
            }
        },
        components: {
            list,
            bulletList,
            imgBodyHorizontal,
            imgBodyVertical,
            box,
            tableList,
        },
        data() {
            return {
                loading: false,
                window: window,
                height: null,
            }
        },
    }
</script>
