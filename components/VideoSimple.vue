<script setup lang="ts">
import { onBeforeUnmount, onMounted, ref } from "vue";

export type VideoProps = {
    url: string,
}

const props = defineProps<VideoProps>();

const videoRef = ref();

const currentTime = ref(0);
const totalTime = ref(null);
const currentVolume = ref(1);
const playing = ref(false);

const timeListener = () => {
    currentTime.value = videoRef.value.currentTime;
}
const durationListener = () => {
    totalTime.value = videoRef.value.duration;
};

const volumeListener = () => {
    currentVolume.value = videoRef.value.volume;
}

const setCurrentVolume = (ev: InputEvent) => {
    videoRef.value.volume = parseFloat((ev.target as HTMLInputElement)!.value);
    currentVolume.value = parseFloat((ev.target as HTMLInputElement)!.value);
}

const handlePlaying = () => {
    playing.value = true;
}

const handlePaused = () => {
    playing.value = false;
}

const togglePlay = () => {
    if (playing.value) {
        // pause the video
        videoRef.value.pause();
        playing.value = false;
    } else {
        videoRef.value.play();
        playing.value = true;
    }
}

onMounted(() => {
    videoRef.value.addEventListener('click', togglePlay);
    videoRef.value.addEventListener('timeupdate', timeListener);
    videoRef.value.addEventListener('durationchange', durationListener);
    videoRef.value.addEventListener('volumechange', volumeListener);
    videoRef.value.addEventListener('playing', handlePlaying);
    videoRef.value.addEventListener('pause', handlePaused);
});

onBeforeUnmount(() => {
    if (videoRef.value) {
        videoRef.value.removeEventListener('click', togglePlay);
        videoRef.value.removeEventListener('timeupdate', timeListener);
        videoRef.value.removeEventListener('durationchange', durationListener);
        videoRef.value.removeEventListener('volumechange', volumeListener);
        videoRef.value.removeEventListener('playing', handlePlaying);
        videoRef.value.removeEventListener('pause', handlePaused);
    }
});

</script>

<template>
    <div class="relative flex items-center justify-center h-[400px] w-auto">
        <video ref="videoRef" class="object-cover h-auto w-full" crossorigin="anonymous" style="aspect-ratio: auto; max-height: 100%;">
            <source :src="props.url" type="video/mp4"/>
        </video>

        <div class="absolute bottom-0 left-0 z-20 bg-pink-500/50 px-8 h-12 w-full flex gap-4 items-center">
            <button v-if="!playing" class="px-2 py-1 bg-teal-500 rounded-md" @click="togglePlay">Play</button>
            <button v-else class="px-2 py-1 bg-red-500 rounded-md" @click="togglePlay" >Pause</button>

            <p>{{ currentTime }}&nbsp;/&nbsp;{{ totalTime }}</p>
        </div>
    </div>
</template>