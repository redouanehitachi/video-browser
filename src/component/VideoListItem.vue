<template>
    <li class="list-group-item media" @click="onVideoSelect">
        <img class="mr-4" :src="thumbnailUrl" alt="">
        <div class="media-body">
            {{ video.snippet.title }}
        </div>
    </li>

</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'],
    computed: {
        thumbnailUrl() {
            return this.video.snippet.thumbnails.default.url
        }
    },
    methods:{
        onVideoSelect(){
            this.$emit('videoSelect',this.video);
        }
    }
}
</script>
<style scoped>
li {
    display: flex;
    cursor: pointer;

}

li:hover {
    background-color: #eee;
}
</style>
