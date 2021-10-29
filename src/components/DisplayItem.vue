<template>
    <div :class="'tree-item ' + item.type">
        <div @click="toggleActive" :class="isActive">
            <div class="icon" :class="isActive"></div>
            <a v-if="item.type == 'link'" :href="item.target">{{ item.name }}</a>
            <span v-else class="item-name">{{ item.name }}</span>
        </div>
        <div v-if="item.type == 'directory'" class="contents" :class="isActive">
            <DisplayItem v-for="i in item.contents" :item="i" :key="i.name" />
        </div>
    </div>
</template>

<script>
    export default {
        name: 'DisplayItem',
        props: {
            item: Object
        },
        data() {
            return {
                isActive: ''
            }
        },
        methods: {
            toggleActive: function() {
                this.isActive = (this.isActive) ? '' : 'active'
            }
        }
    }
</script>

<style>
    .icon {
        display: inline-block;
        width: 1rem;
        height: 1rem;
        margin-right: 0.2rem;
        margin-bottom: -0.1rem;
        background-repeat: no-repeat;
        background-position: left bottom;
    }
    .file .icon {
        background-image: url('/static/icons/file-solid.svg') !important;
    }
    .link .icon {
        background-image: url('/static/icons/link-solid.svg') !important;
    }
    .file .active, .link .active {
        background-color: rgba(143, 211, 248, 0.3) !important;
    }
    .directory .icon {
        background-image: url('/static/icons/folder-solid.svg');
    }
    .directory .icon.active {
        background-image: url('/static/icons/folder-open-solid.svg');
    }
    .directory .contents {
        margin-left: 1rem;
        display: none;
    }
    .directory .contents.active {
        display: block;
    }
    .item-name {
        cursor: default;
    }
</style>
