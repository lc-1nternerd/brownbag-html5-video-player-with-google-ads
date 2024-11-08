---
layout: section
---

# Draw the rest of the f*cking owl 🦉

---


# ... Tadaaaa 🎉

<VideoSimple url="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" />

---

# How do we do that?

Event listeners ... <v-click> a loot of event listeners </v-click>

<v-click>

```js
onMounted(() => {
    videoRef.value.addEventListener('click', togglePlay);
    videoRef.value.addEventListener('timeupdate', timeListener);
    videoRef.value.addEventListener('durationchange', durationListener);
    videoRef.value.addEventListener('volumechange', volumeListener);
    videoRef.value.addEventListener('playing', handlePlaying);
    videoRef.value.addEventListener('pause', handlePaused);
});
```

</v-click>

<v-click>
This gets even more interesting with video seeking and volume changing ...
</v-click>

<br/>

<v-click>
... And then there is styling ... Range inputs are a hell of an element 🫠
</v-click>

<br/>

<v-click>
✨ But it works even CSS only .. quick demo ✨
</v-click>