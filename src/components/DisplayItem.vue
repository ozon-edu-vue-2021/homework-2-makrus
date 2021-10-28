<template>
<div class="tree">
    <div @click="toggleShow" :class="typeClass">
        <div class="icon" :class="typeClass"></div>
        <a v-if="item.type == 'link'" :href="item.target">{{ item.name }}</a>
        <span v-else class="item-name">{{ item.name }}</span>
    </div>
    <div v-if="item.type == 'directory'" class="contents" :class="typeClass">
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
            show: false
        }
    },
    methods:{
        toggleShow: function() {
            this.show = !this.show
        }
    },
    computed: {
        typeClass: function() {
            return (this.show) ? this.item.type + ' active' : this.item.type
        }
    }
}
</script>

<style scoped>
    .icon {
        display: inline-block;
        width: 1rem;
        height: 1rem;
        margin-right: 0.2rem;
        margin-bottom: -0.1rem;
        background-repeat: no-repeat;
        background-position: left bottom;
    }
    .icon.file {
        background-image: url('/static/icons/file-solid.svg');
    }
    .icon.link {
        background-image: url('/static/icons/link-solid.svg');
    }
    .file.active, .link.active {
        background-color: rgba(143, 211, 248, 0.3);
    }
    .icon.directory {
        background-image: url('/static/icons/folder-solid.svg');
    }
    .icon.directory.active {
        background-image: url('/static/icons/folder-open-solid.svg');
    }
    .contents.directory {
        margin-left: 1rem;
        display: none;
    }
    .contents.directory.active {
        display: block;
    }
    .item-name {
        cursor: default;
    }
</style>
