<template>
    <ul class="list-group">
        <VideoListItem 
            v-for="myVideo in videos" 
            :key="myVideo.etag"
            :video="myVideo">
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
    }
};
</script>

<style scoped>

</style>