<template>
<div class="">
    <div @click="toggleShow" :class="(show) ? 'active' : ''">
        <img :src="icon">{{ item.name }}
    </div>
    <div v-if="item.type == 'directory'" v-show="show" class="directory-contents">
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
        let img;
        switch (this.item.type) {
            case 'directory':
                img = './static/icons/folder-solid.svg'
                break
            case 'file':
                img = './static/icons/file-solid.svg'
                break
            case 'link':
                img = './static/icons/link-solid.svg'
                break
        }
        return {
            icon: img,
            show: false
        }
    },
    methods:{
        toggleShow: function() {
            this.show = !this.show
        }
    }
}
</script>

<style scoped>
    img {
        max-width: 1rem;
        max-height: 1rem;
        margin-right: 0.2rem;
    }
    .directory-contents {
        margin-left: 1rem;
    }
    .active {
        background-color: rgba(143, 211, 248, 0.3);
    }
</style>
