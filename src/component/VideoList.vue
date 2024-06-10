<template>
    <ul class="list-group col-md-4">
        VideoList
        <VideoListItem v-for="video in videos" :video="video" :key="video.etag" @videoSelect="onVideoSelect" />

    </ul>

</template>
<script>
import VideoListItem from './VideoListItem.vue';
export default {
    name: 'VideoList',
    props: ['videos'],
    components: {
        VideoListItem
    }, methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video)
        }
    },

}
</script>
<style></style>./VideoList.vue