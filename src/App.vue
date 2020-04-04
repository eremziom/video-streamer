<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
            <VideoDetail :video="selectedVideo"/>
            <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import VideoDetail from './components/VideoDetail.vue';
import VideoList from './components/VideoList.vue';
const API_KEY = 'AIzaSyBTEQmwXJUPsYXJ1mzf7EvK3go8CGJCk_U';
export default {
    name: 'App', // need mostly for debugging
    components: {
        SearchBar,
        VideoList,
        VideoDetail,
    },
    data(){
        return{
            videos: [],
            selectedVideo: null
        }
    },
    methods: {
        onTermChange(searchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            })
            .then(response => {
                this.videos = response.data.items;
            });
        },
        onVideoSelect(video){
            this.selectedVideo = video;
        }
    }
}
</script>