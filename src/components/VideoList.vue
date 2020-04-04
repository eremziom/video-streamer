<template>
    <ul class="list-group col-md-4">
        <VideoListItem 
            v-for="myVideo in videos" 
            :key="myVideo.etag"
            :video="myVideo"
            @videoSelect="onVideoSelect">
        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem.vue';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: Array
    },
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video)
        }
    }
};
</script>

<style scoped>

</style>