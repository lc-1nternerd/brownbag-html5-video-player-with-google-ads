---
layout: section
---

# Now lets do <span class="italic bg-gradient-linear shape-[100deg] bg-gradient-from-pink-300 bg-gradient-via-yellow bg-gradient-to-blue bg-clip-text color-transparent leading-2 px-2">Ads</span>

---

# Googles' side of things

- Google has an SDK for integrating video ads called [IMA Sdk](https://developers.google.com/interactive-media-ads/docs/sdks/html5/client-side)
    - It also provides [quite useful testing tools for this](https://googleads.github.io/googleads-ima-html5/vsi/)
- It mainly uses a format called VAST (_Video Ad Serving Template_&nbsp;) and can thus communicate with all compliant servers
    - so basically not only Google Ads servers
    - And there is also other formats (but honestly I have no idea what dem do atm)
- VAST is an XML format that can define multiple ad slots before/during/after a video sequence:

---

# VAST exãmplē

```xml
<vmap:VMAP xmlns:vmap="http://www.iab.net/videosuite/vmap" version="1.0">
    <vmap:AdBreak timeOffset="start" breakType="linear" breakId="preroll">
        <vmap:AdSource id="preroll-ad-1" allowMultipleAds="false" followRedirects="true">
            <vmap:AdTagURI templateType="vast3">
                <![CDATA[ https://pubads.g.doubleclick.net/gampad/ads?slotname=/21775744923/external/vmap_ad_samples&sz=640x480&ciu_szs=300x250&cust_params=sample_ar%3Dpremidpost&url=&unviewed_position_start=1&output=xml_vast3&impl=s&env=vp&gdfp_req=1&ad_rule=0&useragent=Mozilla/5.0+(Macintosh%3B+Intel+Mac+OS+X+10_15_7)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/130.0.0.0+Safari/537.36,gzip(gfe)&vad_type=linear&vpos=preroll&pod=1&ppos=1&lip=true&min_ad_duration=0&max_ad_duration=30000&vrid=1264775&cmsid=496&video_doc_id=short_onecue&kfa=0&tfcd=0 ]]>
            </vmap:AdTagURI>
        </vmap:AdSource>
    </vmap:AdBreak>
    <vmap:AdBreak timeOffset="00:00:15.000" breakType="linear" breakId="midroll-1">
        <vmap:AdSource id="midroll-1-ad-1" allowMultipleAds="false" followRedirects="true">
            <vmap:AdTagURI templateType="vast3">
                <![CDATA[ https://pubads.g.doubleclick.net/gampad/ads?slotname=/21775744923/external/vmap_ad_samples&sz=640x480&ciu_szs=300x250&cust_params=sample_ar%3Dpremidpost&url=&unviewed_position_start=1&output=xml_vast3&impl=s&env=vp&gdfp_req=1&ad_rule=0&cue=15000&useragent=Mozilla/5.0+(Macintosh%3B+Intel+Mac+OS+X+10_15_7)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/130.0.0.0+Safari/537.36,gzip(gfe)&vad_type=linear&vpos=midroll&pod=2&mridx=1&rmridx=1&ppos=1&lip=true&min_ad_duration=0&max_ad_duration=30000&vrid=1264775&cmsid=496&video_doc_id=short_onecue&kfa=0&tfcd=0 ]]>
            </vmap:AdTagURI>
        </vmap:AdSource>
    </vmap:AdBreak>
...
</vmap:VMAP>
```

---

# Enough talking dipshit, how do you integrate for the sweet sweet 💰🤑??
<v-click>

We basically need a parent element that wraps both the native `<video>` element and the Google Ad container.

The pesudo-code structure for this will look something like this:

```html
<wrapper-el style="position: relative">
    <video>
        <source />
        <!-- possibly also text tracks -->
    </video>
    <ad-wrapper style="position: absolute; z-index: 10; top:0; left:0; height:100%; width: 100%"></ad-wrapper>
    <custom-video-controls style="position: absolute; z-index: 10; width: 100%"></custom-video-controls>
</wrapper-el>
```

</v-click>

---
layout: section
---

# Hooow long do you want to edge me senpai??

Ook ok, we'll take a look at some code nau(.ch)  
_aka es is 11:40 und i hab ka zeit für a full fledged demo_