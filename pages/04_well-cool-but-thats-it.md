---
layout: section
---

# Cool story bruh, but is that all we can do here?
<v-click>
    <span class="text-5xl">🥁🥁🥁</span>
</v-click>

---

# Of course not

- Google supports tracking events for dem user insights
- We can have companion ads around the video, for mooar ad real estate
- ... but Google IMA SDK does a lot behind the scenes already, like 
    - _Active view measurement_ to track how much of an ad has been viewed (if the video player supports skippable ads)
    - integrates with the Open Measurement Interface definition for ad performance tracking of third-parties
    - ...

for ref:
https://developers.google.com/interactive-media-ads/docs/sdks/html5/client-side

---

# And how stupid is it to build this shit on your own??

- probably somehwat maybe possibly _a looot_? 🤷‍♂️
<v-click>  

- but it is likely better to focus on the minimal requirements than to integrate a full-fleged 40kb library like [video.js](https://github.com/videojs/video.js/)
    - of course depending on the scenario
</v-click>
<v-click>

- And surely there are solutions out there that help with ads
    - [video.js](https://github.com/videojs/video.js/)
    - [media-chrome](https://www.media-chrome.org/)
    - and nice themes (and or inspiration) [ref](https://player.style/)
    - ... these are all done by _mux_ 
</v-click>