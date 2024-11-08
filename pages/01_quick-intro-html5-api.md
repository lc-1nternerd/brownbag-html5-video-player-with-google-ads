---
layout: section
---

# Quick intro on the HTML5 Media API
Or rather the `HTMLMediaElement`  
[MDN reference](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement)

---

# HTMLMediaElement

- Allows for programmatic access to a Media Element _duh_ - namely `<audio>` & `<video>`
- We can query values like `currentTime`, `textTracks`, `volume` etc.
- Aaand we can also call methods like `play`, `pause`, `captureStream` <span class="text-xs text-neutral-400">(eg. for a WebRTC Video streaming)</span>

<br/>
<br/>
<br/>

<v-click> 
    As with many vanilla JS things out there, there is one flaw we need to overcome for the modern web ...
</v-click>


<v-click> 
    <div class="w-full text-center mt-4">
    <span class="text-3xl italic bg-gradient-linear shape-[100deg] bg-gradient-from-pink bg-gradient-via-teal bg-gradient-to-purple bg-clip-text color-transparent text-3xl px-2">reactivity</span>
    </div>
</v-click>

---

# JS API Demo


<div class="flex flex-wrap gap-4">
    <video controls class="w-[400px]" id="demo-vid" crossorigin="anonymous">
        <source src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" type="video/mp4" />
    </video>
    <div class="flex flex-col gap-4">
        <div class="flex gap-4">
            <button id="demo-play" class="px-2 py-1 bg-teal-500 rounded-md">Play</button>
            <button id="demo-pause" class="px-2 py-1 bg-red-500 rounded-md">Pause</button>
        </div>
        <div class="flex gap-4">
            <button id="demo-playback" class="px-2 py-1 bg-blue-500 rounded-md">Set playback speed to 1.6</button>
        </div>
    </div>
</div>


```ts {monaco-run}
const demoVid = document.getElementById("demo-vid");

const play = document.getElementById("demo-play");
const pause = document.getElementById("demo-pause");
const playback = document.getElementById("demo-playback");

play.addEventListener("click", () => {
    demoVid.play();
});

pause.addEventListener("click", () => {
    demoVid.pause();
});

playback.addEventListener("click", () => {
    demoVid.playbackRate = 1.6;
});
```
