<template>
    <div class="container ">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">

            <VideoDetails :video="selectedVideo" />
            <VideoList :videos="videos" @videoSelect="onVideoSelect" />
        </div>

    </div>

</template>
<script>
import SearchBar from './component/SearchBar';
import VideoList from './component/VideoList';
import axios from 'axios';
import VideoDetails from './component/VideoDetails.vue';
const API_KEY = 'AIzaSyC8G2saLKe5kqMYD-n4bsXmIOxQ-bpmyGY';

export default {
    name: 'App',
    data: function () {
        return {
            videos: [], selectedVideo: null
        }
    },
    components: {
        SearchBar, VideoList,
        VideoDetails
    },
    methods: {
        onTermChange: function (searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
            })
        },
        onVideoSelect(video) {
            this.selectedVideo = video;
        }

    },
}
</script>